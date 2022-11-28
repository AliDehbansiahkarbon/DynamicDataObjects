# DynamicDataObjects
This Delphi code library lets you model structured data and serialze to/from a variety of data serialization formats such as:
CBOR, JSON, MessagePack, ION, UBJSON, BSON, Smile, DataObj, CSV, ICS, BinaryJData, etc.  Most of these serializations are complete such as JSON, BSON, CBOR, DataObj, but some of the more obscure ones are coded but are only minimally tested.

What makes this implementation different from other JSON or BSON or MessagePack or CBOR libraries, etc. is that this library uses one set of objects for modeling data in a consistent way, and then multiple serializers can serialize to/from that object model.  Most of the other serialization libraries out there are only designed to serialize to the one and only one format that they are coded for.  So, if you have a project that needs to serialize CBOR, JSON and BSON, you end up having three separate libraries that all have different objects, properties and methods to use to put data into and extract data out of.  This code library allows you to use one common object "TDataObj" to model hierarchial data and then you can serialize to/from using any of the serialization formats that you choose to include. 

If you have a project that will use two or more serializations, such as JSON with BSON or JSON with CBOR, then this is a very good library to consider as it will give you consistency, high performance and save you in development time. 

This project is primarily coded and tested with Delphi 10.4 and Delphi 11.  It has not been tested with older Delphi versions or other pascal compilers, but likely it will work just fine with some minor tweaks. 

A significant amount of attention has been placed on serialization performance, especially with CBOR, DataObj, BSON and JSON because I use these four the most.  With JSON, it's faster than Embarcadero's multiple JSON implementations under most situations.  The JSON serialization has been extensively compared performance-wise to a few of the other popular JSON libraries for Delphi out there.  Most of them are so extremely slow that I stopped comparing with them.  The three that I found to be the best performance-wise are embarcadero's system.json, Grijjy, DDO, and this code.    

This code is extremely easy to use, you only need to include DataObjects2.pas in your project.  Then, to choose one or more serializers to also be included, simply include those units as well.  

There are a few future features that we have planned such as:
  1.  Geometry data types (The DDO format supports it direcly),
  2.  Direct RTTI object serialization,
  3.  Sparse arrays (somewhat coded already but not fully baked),
  4.  Completing JSON5 support (partially supported now).
  5.  YAML serialization support.
  6.  Comment support (usable by YAML and JSON5)
  7.  Better CBOR tag interpretation.


Each serializer class may introduce some properties that affect the serialization.  For example, the JSON serializer can produce with tight formatting or human text readable formatting. The JSON serialization supports ASCII, ANSI, UTF8, UTF7 or Unicode character encodings. 

I have three general purpose executables that are built upon this library:  A standalone editor executable called the DataObject Editor, a windows explorer previewer dll so these file types can be viewed directly in the preview pane, and a Delphi plugin that lets you see the data within a DataObject while debugging.  The source code for these applications are not yet made public as they are just not quite baked enough, but they are coming.
