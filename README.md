import java.util.ArrayList;
import java.util.List;

public class Car {
    private String make;
    private String model;
    private int year;
    private boolean rented;
    
    public Car(String make, String model, int year) {
        this.make = make;
        this.model = model;
        this.year = year;
        this.rented = false;
    }
    
    public String getMake() {
        return make;
    }
    
    public String getModel() {
        return model;
    }
    
    public int getYear() {
        return year;
    }
    
    public boolean isRented() {
        return rented;
    }
    
    public void setRented(boolean rented) {
        this.rented = rented;
    }
    
    public String toString() {
        return make + " " + model + " (" + year + ")";
    }
}

public class CarRentalSystem {
    private List<Car> cars;
    
    public CarRentalSystem() {
        this.cars = new ArrayList<Car>();
    }
    
    public void addCar(Car car) {
        cars.add(car);
    }
    
    public List<Car> availableCars() {
        List<Car> availableCars = new ArrayList<Car>();
        for (Car car : cars) {
            if (!car.isRented()) {
                availableCars.add(car);
            }
        }
        return availableCars;
    }
    
    public void rentCar(Car car) {
        if (!car.isRented()) {
            car.setRented(true);
            System.out.println("Rented " + car);
        } else {
            System.out.println(car + " is not available for rent");
        }
    }
    
    public void returnCar(Car car) {
        if (car.isRented()) {
            car.setRented(false);
            System.out.println("Returned " + car);
        } else {
            System.out.println(car + " was not rented");
        }
    }
    
    public static void main(String[] args) {
        CarRentalSystem rentalSystem = new CarRentalSystem();
        
        // Add some cars to the system
        rentalSystem.addCar(new Car("Toyota", "Camry", 2019));
        rentalSystem.addCar(new Car("Honda", "Accord", 2020));
        rentalSystem.addCar(new Car("Nissan", "Altima", 2018));
        
        // Rent a car
        List<Car> availableCars = rentalSystem.availableCars();
        if (!availableCars.isEmpty()) {
            rentalSystem.rentCar(availableCars.get(0));
        }
        
        // Return the car
        rentalSystem.returnCar(availableCars.get(0));
    }
}
