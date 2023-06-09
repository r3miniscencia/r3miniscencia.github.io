- Véase [[Flujo de trabajo]]
- query-table:: false
  > 🔨 Now (haciendo)
  {{query (todo doing)}}
- ## ⏰ Hoy
  query-table:: false
	- ### 🔥 Tareas ==vencidas==
	  query-table:: false
	  Deadline en el pasado y no están finalizadas
	    #+BEGIN_QUERY
	    {
	        :query [
	            :find (pull ?block [*])
	            :in $ ?today
	            :where
	                        [?block :block/marker ?m]
	                        [(contains? #{"TODO"} ?m)]
	                        [?block :block/deadline ?d]
	                        [(< ?d ?today)]
	        ]
	    :result-transform (fn [result]
	        (sort-by (fn [d]   (get d :block/deadline)
	        ) result))
	        :inputs [:today]
	        :breadcrumb-show? false
	        :collapsed? false
	    }
	    #+END_QUERY
	- ### 🔥  Vencen hoy
	  query-table:: false
	  Deadline hoy
	  #+BEGIN_QUERY
	    {
	        :query [
	            :find (pull ?block [*])
	            :in $ ?today
	            :where
	                        [?block :block/marker ?m]
	                        [(contains? #{"TODO"} ?m)]
	                        [?block :block/deadline ?d]
	                        [(= ?d ?today)]
	        ]
	    :result-transform (fn [result]
	        (sort-by (fn [d]   (get d :block/deadline)
	        ) result))
	     :inputs [:today]
	     :breadcrumb-show? false
	     :collapsed? false
	    }
	    #+END_QUERY
	- ### 🌞 Para hoy
	  Scheduled  para hoy o mencionan la fecha de hoy
	  #+BEGIN_QUERY
	  {
	      :query [
	          :find (pull ?block [* {:block/refs [:block/journal-day]}])
	          :in $ ?today
	          :where
	              (or-join [?block ?today] 
	                  (and
	                      [?block :block/marker ?m]
	                      [(contains? #{"TODO"} ?m)]
	                      [?block :block/scheduled ?d]
	                      [(= ?d ?today)]
	                  )
	                  (and
	                      [?block :block/refs ?p]
	                      [?p :block/journal? true]
	                      [?p :block/journal-day ?d]
	                      [(= ?d ?today)]
	                  )
	              )
	      ]
	     :result-transform (fn [result]
	        (sort-by (fn [d]  (or (get (get d :block/ref-pages) :page/journal-day)
	                                               (get d :block/scheduled) 
	                                               (get d :block/deadline)
	         )) result))
	      :inputs [:today]
	      :breadcrumb-show? false
	      :collapsed? false
	  }
	  #+END_QUERY
	- ### ⛅ Continuar con...
	  Scheduled en el pasado y aún no finalizadas
	  #+BEGIN_QUERY
	  {
	      :query [
	          :find (pull ?block [*])
	          :in $ ?today
	          :where
	                      [?block :block/marker ?m]
	                      [(contains? #{"TODO"} ?m)]
	                      [?block :block/scheduled ?d]
	                      [(< ?d ?today)]
	      ]
	     :result-transform (fn [result]
	        (sort-by (fn [d]  (or (get (get d :block/ref-pages) :page/journal-day)
	                                               (get d :block/scheduled) 
	                                               (get d :block/deadline)
	         )) result))
	      :inputs [:today]
	      :breadcrumb-show? false
	      :collapsed? false
	  }
	  #+END_QUERY
- ## 📆 Mañana
  query-table:: false
  collapsed:: true
  Planificadas, deadlines o mencionadas
  #+BEGIN_QUERY
  {
      :query [
          :find (pull ?block [* {:block/refs [:block/journal-day]}])
          :in $ ?tomorrow
          :where
              (or-join [?block ?tomorrow] 
                  (and
                      [?block :block/marker ?m]
                      [(contains? #{"TODO"} ?m)]
                      (or [?block :block/scheduled ?d] [?block :block/deadline ?d])
                      [(= ?d ?tomorrow)]
                  )
                  ;; 2nd case: the date linked from the block is in the 7day window
                  (and
                      [?block :block/refs ?p]
                      [?p :block/journal? true]
                      [?p :block/journal-day ?d]
                      [(= ?d ?tomorrow)]
                  )
              )
      ]
     :result-transform (fn [result]
        (sort-by (fn [d]  (or (get (get d :block/ref-pages) :page/journal-day)
                                               (get d :block/scheduled) 
                                               (get d :block/deadline)
         )) result))
      :inputs [:tomorrow]
      :breadcrumb-show? false
      :collapsed? false
  }
  #+END_QUERY
- ## 📅 Resto de la semana
  query-table:: false
  collapsed:: true
  Con deadline, scheduled o fecha mencionada en los próximos 7 diás a partir de mañana
  #+BEGIN_QUERY
  {
      :query [
          :find (pull ?block [* {:block/refs [:block/journal-day]}])
          :in $ ?start ?next
          :where
              (or-join [?block ?start ?next] 
                  (and
                      [?block :block/marker ?m]
                      [(contains? #{"TODO"} ?m)]
                      (or [?block :block/scheduled ?d] [?block :block/deadline ?d])
                      [(>= ?d ?start)]
                      [(<= ?d ?next)]
                  )
                  ;; 2nd case: the date linked from the block is in the time window
                  (and
                      [?block :block/refs ?p]
                      [?p :block/journal? true]
                      [?p :block/journal-day ?d]
                      [(>= ?d ?start)]
                      [(<= ?d ?next)]
                  )
              )
      ]
      :result-transform (fn [result]
        (sort-by (fn [d]
            (get d :block/deadline 
            (get d :block/scheduled
            (get (last (get d :block/refs)) :block/journal-day 
             99999999999)))
           )
        result))
      :inputs [:2d-after :7d-after]
      ;; :view (fn [result] (for [r result] [:pre (pr-str r)]))
      :breadcrumb-show? false
      :collapsed? false
  }
  #+END_QUERY
- ## 🌗 Tareas "sin día"
  query-table:: false
  Items marcados "to-do" sin deadline ni scheduled
  #+BEGIN_QUERY
  {
      :query [
          :find (pull ?block [* {:block/refs [:block/journal-day]}])
          :where
                      [?block :block/marker ?m]
                      [(contains? #{"TODO"} ?m)]
                      (not [?block :block/scheduled ?d])
                      (not [?block :block/deadline ?d]) 
      ]
      :result-transform (fn [result]
        (sort-by (fn [d]
            (get (last (get d :block/refs)) :block/journal-day 
             99999999))
        result))    
      :breadcrumb-show? true
      :collapsed? false
  }
  #+END_QUERY
- ## ⏳ Esperando...
  query-table:: true
  query-properties:: [:Date? :block]
  Items marcados con "waiting", mera lista de items, ordenados por la fecha en que se crearon (más recientes primero)
  #+BEGIN_QUERY
  {:query [
      :find (pull ?b [* {:block/refs [:block/journal-day]}])
      :where
           [?b :block/marker ?m]
           [(contains? #{"WAITING"} ?m)]
           ]
      :result-transform (fn [result]
           (defn get-date [d] 
               (-> d :block/page :block/journal-day))
           (defn add_date [block]
               (update block :block/properties (fn [prop] (assoc prop :Date? (get-date block))))
           )
           (reverse (sort-by get-date (map add_date result)))
       )
   :breadcrumb-show? false
   ; :view (fn [result] (for [r result] [:pre (pr-str r)])) 
   :collapsed? false
  }
  #+END_QUERY