# Diamond

A proposal for a markdown syntax for diagrams

## Why?

Because diagrams on computers currently suck.

Almost all diagrams on computers are stored in proprietary-format binary files or image files.

They are not indexable, searchable or version-controllable.

They are a pain to embed alongside other content, to link to from other content, and to manage links
to from other content.

The programs available to edit them encourage their users (well, me anyway) to burn time on layout,
style and formatting, instead of actually thinking about the content and expressing oneself simply,
visually.

Arguably, the situation was better when Microsoft ruled the world, and MS Word and Visio operated to
some extent as de facto standards, and interoperated reasonably well. But if this was ever the case
for a while, it isn't any more.

The web offers the promise of content organized into coherent chunks and joined together by references
(links), eliminating repetition and enhancing knowledge - Wikipedia is clearest example.

But owing to the sucky situation with diagrams, this content is largely text, with a few pictures
scattered around.



## How?

By starting with identifying some key principles of a markdown:
* It MUST be readable enough and memorable enough for users to work with the source directly, without
  any tool more sophisticated than a text editor.
* It must be line-oriented, to play nicely with code control systems.
* It separates concerns: representing content, not layout or styling.
* It prizes simplicity.

Throw in a few principles specifically around diagrams:
* Prefer "universal" visual conventions that we think everyone intuitively understands, over ones
  that have to be learnt (ahem, UML). For example:
  * Some words in a shape = a specific idea or concept
  * A line between two shapes = a connection between the two concepts
  * An arrowhead at one end of the line = the connection is asymmetric - directed in some way
  * A shape inside another shape = a concept that belongs to, or is a sub-set of, another concept
  * And, err, that's it...

Get inspiration from what's already out there, in particular:
* Graphviz
* flowchart.js



## What?

1. Genesis
  1. A block of words (a single line or multiple consecutive lines) become text in a shape (default shape is a box)
  2. Borrowing from Graphviz, the " -- " symbol represents a symmetric connection between two concepts, or, in more
     mathematical language, an undirected edge between two nodes.
  3. The " -> " symbol represents an unsymmetric connection, a directed edge.
  4. The " (- " symbol represents "belongs to", looking a little like the "element of" symbol in set notation. Hence
     "A (- B" would be drawn as a box labelled "B" containing another box labelled "A".
  5. The above two symbols can be reversed.

2. Exodus
  4. We will often want to represent multiple connections to/from the same shape, without having to re-type the
     whole text of the concept.
  5. We will (despite the simplicity principle!) want to represent different kinds of concept by using different
     shapes, so we might as well tackle that now in a way that avoids breaking the separation of concerns principle
     too!
  6. So we introduce the attributes of identifier, label and type to the node, and while we're about it, we might as
     well give them to the edge as well:
     1. identifier [type] "label"
     2. where identifier and type are both: [a-zA-Z0-9_-\.]+
     3. all are optional, if label is not specified then identifier is used
     4. when applied to an edge, they are placed inside the edge symbol, with two extra dashes, e.g.
        --[normal] "Approved"->
        --[exception] "Declined"->
     5. nodes can be referenced subsequently using just the identifier

3. Leviticus
  1. 2.6.5 above introduces the possibility of inconsistency into the spec - the same node can be defined mulitple
    times (i.e. by having the same identifier), but being given different a type and/or label.
  2. The renderer should use the final specification values given, but is allowed to report such inconsistencies,
    but without obscuring the diagram.




## Where?



## When?




## Who?

