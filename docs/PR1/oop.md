# Objektorientierte Programmierung

So, wie statische Attribute **Klassenvariablen** genannt werden, sind statische Methoden **Klassenmethoden**.

## Statische Factory-Methoden

````java
// (1)
public static Room createRoom(Scanner in) {
    double area = in.nextDouble();
    int seatCount = in.nextInt();
    String name = in.next();
    
    return new Room(area, seatCount, name);
}
````

1. Voraussetzung: Eingabedaten sind in der Eingabequelle in der richtigen Reihenfolge und im richtigen Format vorhanden.

````java
public static RoomList createRooms(Scanner in) {
    RoomList list = new RoomList();
    
    while (in.hasNext()) {
        list.add(createRoom(in));
    }
    return list;
}
````




