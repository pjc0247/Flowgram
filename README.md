# Flowgram

Context based bot engine.

```cs
[Command("/reservation")]
class Reservation : Dialogue {
  public void Begin() {
  
    Choice(
      "Please select a menu", 
      new string[] {
         "Chicken Soup",
         "Beef Steak",
         "Just Water"
      });
    SetNext("Menu");
  }
  
  public void Menu(string menu) {
    Reply($"Your choice: {menu}");
    
    Reply("Please let us know when you can come");
    
    SetNext("Time");
  }
  
  public void Time(DateTime time) {
    Choice(
      "CHECK YOUR RESERVATION, (time, menu...)", 
      new string[] {
         "OK",
         "Cancel"
      });
    SetNext("Confirmation");
  }
  
  public void Confirmation(string selection) {
    if (selection == "OK") 
      Reply("Done! Thank you.");
    else 
      Goto("Begin");
  }
}
```
