Composable Onboard Workflows - 

This NIP adds a way to generate an event-id that can be shared with someone yet to join nostr. A client can request this ID as part of their on-boarding process and pull down the information the host composed for the new user.

---

-   The hostee creates a note containing the following information:
    
    -   The host relay that will store the note, tagged as `hostrelay`
    -   Recommended relays tagged as `relays`
    -   Recommended pubkeys tagged as `p`
    -   A pet name for the invitee tagged as `petname`
   
-    The invitee shares the event-id of the note with the new user.
    
-    The new is asked by the client if they have a invite event, if provided the client requests the note from the host relay.
    
-   The client may renders a welcome message for the new user, using the information in the note.



Here is an example of the note that the invitee could create:

```
{
  "pubkey": "alice",
  "kind": 1989,
  "tags": [
    ["hostrelay", "wss://relay.example.com"],
    ["relays", "wss://relay.example.com", "wss://relay2.example.com"],
    ["p", "bob", "carol", "zach"],
    ["petname", "John Smith"],
  ],
  ...
}
```
Here is an example of the welcome message that the client could render:

```
Welcome, John Smith! Alice has some recommendations for you:

* Try these relays: (click here to add them all)
    * wss://relay.example.com
    * wss://relay2.example.com
* Connect with these people: (click here to follow them all)
    * alice (invited you)
    * bob
    * carol
    * zach
```
