---
layout: post
title: The Ruby Enumerable module
---

Recently I have come across the different ways you can iterate on a collection in Ruby.

Given an array which holds 3 different values, X, O or -, I wanted to iterate through the array and get back which indices had `-`.

In the case of Java I would probably loop through and then check if the item matched the free marker (-) and then add this to another return collection.

{% highlight ruby %}
public List<Integer> possibleMoves() {
  List<Integer> possibleMoves = new ArrayList<Integer>();
  for (int i = 0; i < positions.length; i++) {
    if (positions[i] == Marker.EMPTY.asChar()) {
     possibleMoves.add(i);
    }
  }
  return possibleMoves;
}
{% endhighlight %}

My first attempt in Ruby involved using the `each_with_index` and `inject` methods from the Enumerable module.

{% highlight ruby %}
def available_positions
  positions.each_with_index.inject([]) do |avail_positions, (value, index)|
    avail_positions << index if value == '-'
    avail_positions
  end
end
{% endhighlight %}

I then found out that there is a better way to do this using `each_index` and `select` to filter out the values you want to keep.

{% highlight ruby %}
def available_positions
  positions.each_index.select { |index| positions[index] == '-' }
end
{% endhighlight %}

This goes to show that there are many ways to solve a problem. 
Over the years of people giving you feedback, the odd Google search and actually reading some docs, you will gain the experience to recognise there's a better way.

### Sources

[Enumerable Docs][1]

[SO question][2]

[1]: http://ruby-doc.org/core-2.2.2/Enumerable.html
[2]: http://stackoverflow.com/questions/13659696/find-indices-of-elements-that-match-a-given-condition


