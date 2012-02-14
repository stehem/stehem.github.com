---
layout: post
title: Pascal's triangle in Clojure
description: How to generate a Pascal's triangle with Clojure
tags: [clojure]
---

Pascal's triangle is a rather simple mathematics construct where each member of the subsequent lines is the sum of the two members directly above it in the triangle. Pascal's triangle is described in details [here](http://en.wikipedia.org/wiki/Pascal%27s_triangle)

{% highlight clojure %}

(require 'clojure.string)
(require 'clojure.java.io)

(ns clojure.test.pascal-triangle)


(def new+ (fnil + 0))

(defn with-indexes
  [mylist]
  (map-indexed list mylist)
)

(defn previous
  [indexedline index]  
  (first (filter #(= (- index 1) (first %)) indexedline))
)

(defn sum
  [indexedline member]
  (new+ (second (previous indexedline (first member))) (second member))
)   

(defn new-line
  [indexedline]
  (->>
    (reduce
      (fn[memo f] (concat (list (sum indexedline f)) memo)) (list) indexedline
    )
    (concat (list (second (last indexedline))))
    (reverse)
  )
)

(defn generate-triangle
  [result i]
  (if (= 0 i)
    (reverse result)
    (recur (concat (list (new-line (with-indexes (last (reverse result))))) result) (dec i)))
)
    
(defn triangle
  [start-value number-of-lines]
  (generate-triangle (list (list start-value)) number-of-lines) 
)

(doseq [line (triangle 1 8)] (println (apply str (repeat (- 9 (count line)) " ")) line))

{% endhighlight %}



