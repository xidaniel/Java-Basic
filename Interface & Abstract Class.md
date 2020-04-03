## Why do we use interface ?
   - It likes a protocol to standardize the signature of the method.
   - Varialbes are public, static, final type.
   - It is implemented by using a class.
   - It is used to achieve total abstraction.
   - Since java does not support multiple inheritance in case of class, but by using interface it can achieve multiple inheritance .
   - It is also used to achieve loose coupling.
   - Interfaces are used to implement abstraction.
   - The reason is, abstract classes may contain non-final variables, whereas variables in interface are final, public and static.
   
 

## Coding Example:
__________________________________________________________

            public interface Device {
                int getVoltage();
            }
__________________________________________________________

            public class Vehicle {

                private String color; // What color are we?
                private String model; // What model vehicle are we?

                public Vehicle(String color, String model) {
                    this.color = color;
                    this.model = model;
                }

                public String getColor() {
                    return color;
                }

                public void setColor(String color) {
                    this.color = color;
                }

                public String getModel() {
                    return model;
                }

                public void setModel(String model) {
                    this.model = model;
            }
        }

__________________________________________________________

            public class Car extends Vehicle implements Device {

                private int year; // Year of our car
                private int voltage; // Battery voltage
                private static int wheels; // How many wheels do we have

                public Car(String color, String model, int year) {
                    super(color, model);
                    this.year = year;
                    this.voltage = 12;
                }

                @Override
                public int getVoltage() {
                    return voltage;
                }

                public int getYear() {
                    return year;
                }

                public void setYear(int year) {
                    this.year = year;
                }

                public static int getWheels() {
                    return wheels;
                }

                public static void setWheels(int count) {
                    wheels = count;
                }

                public String toString() {
                    return "Car: " + getColor() + " : " + getModel() + " : " + getYear();
                }
            }
