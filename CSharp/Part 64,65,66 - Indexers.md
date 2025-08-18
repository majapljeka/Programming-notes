What are Indexers?

Indexers allow instances of a class to be indexed just like arrays.

Indexers in asp.NET

```
Session["Session1"] = "Session 1 Data";
Session["Session2"] = "Session 2 Data";

Response.Write("Session 1 Data = " + Session[0].ToString());

Response.Write("Session 2 Data = " + Session[Session2].ToString());
```
