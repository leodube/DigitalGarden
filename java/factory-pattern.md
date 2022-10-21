#java #pattern

For this use case, we want to combine the first letter of the make, the first letter of the model, and the year for a given vehicle to create a vehicle code. Rather than call a method inside a constructor:

```java
class Vehicle {
	private String make;
	private String model;
	private int year;
	private String code;

	Vehicle(String ma, String mo, int y) {
		make = ma;
		model = mo;
		year = y;
		code = generateCode(); // <-- avoid calling methods inside constructor!
	}

	private static String generateCode() {
		// implementation
	}
}
```

We can use a factory class to create the Vehicle class, then call the required method, and finally return the completed Vehicle class.

```java
//usage
VehicleFactory vf = new VehicleFactory();
Vehicle v = vf.createVehicle("Dodge", "Charger", 2007);

class VehicleFactory {
	public static Vehicle createVehicle(String ma, String mo, String y) {
		Vehicle v = new Vehicle(ma, mo, y);
		v.generateCode();
		return v;
	}
}

class Vehicle {
	private String make;
	private String model;
	private int year;
	private String code;
	
	Vehicle(String ma, String mo, int y) {
		make = ma;
		model = mo;
		year = y;
		code = generateCode();
	}

	public static String generateCode() {
		// implementation
	}
}
```