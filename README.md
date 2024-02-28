package com.home;

import java.util.HashMap;
import java.util.Map;

public class House 
{
	
	private Map<String, room> rooms;
	

    public House() {
		//super();
		this.rooms = new HashMap<>();
		
	}

    public void addRoom(String roomName) 
    {
        rooms.put(roomName, new room(roomName));
    }

    public room getRoom(String roomName) 
    {
        return rooms.get(roomName);
    }

	public void displayStatus()
	{
        System.out.println("House Status:");
        for (room room : rooms.values()) 
        {
            room.displayStatus();
        }
    }

	public void totalTimeInCurrentState() {
		// TODO Auto-generated method stub
		
	}

public interface Device {

	String getName();

    boolean isOn();

    void turnOn();
    
    void turnOff();

    long getTotalTimeInCurrentState();
}

public class Electronicdevice implements Device {

	String name;
    boolean isOn;
     long totalTimeInCurrentState;
	
     public Electronicdevice(String name) 
     {
         this.name = name;
     }

     @Override
     public String getName() 
     {
         return name;
     }

     @Override
     public boolean isOn()
     {
         return isOn;
     }

     @Override
     public void turnOn() 
     {
         isOn = true;
         
         totalTimeInCurrentState += System.currentTimeMillis();
     }

     @Override
	public void turnOff() 
	{
		isOn = false;
         
         totalTimeInCurrentState -= System.currentTimeMillis();
		
	}

	@Override
     public long getTotalTimeInCurrentState() 
     {
         return totalTimeInCurrentState;
     }
 
}

public class AC extends Electronicdevice
{

	public AC(String name) 
	{
		super(name);
		// TODO Auto-generated constructor stub
	}

	@Override
    public String getName() 
    {
        return name;
    }

    @Override
    public boolean isOn()
    {
        return isOn;
    }

    @Override
    public void turnOn() 
    {
        isOn = true;
        
        totalTimeInCurrentState += System.currentTimeMillis();
    }
    
   @Override
	public void turnOff() 
    {
    	isOn = false;
        
        totalTimeInCurrentState -= System.currentTimeMillis();
	}

	@Override
    public long getTotalTimeInCurrentState() 
    {
        return totalTimeInCurrentState;
    }
}

public class Light extends Electronicdevice
{

	public Light(String name) 
	{
		super(name);
		// TODO Auto-generated constructor stub
	}

	@Override
    public String getName() 
    {
        return name;
    }

    @Override
    public boolean isOn()
    {
        return isOn;
    }

    @Override
    public void turnOn() 
    {
        isOn = true;
        
        totalTimeInCurrentState += System.currentTimeMillis();
    }

    
    @Override
	public void turnOff() 
    {
    	isOn = false;
        
        totalTimeInCurrentState -= System.currentTimeMillis();
	}

	@Override
    public long getTotalTimeInCurrentState() 
    {
        return totalTimeInCurrentState;
    }

}

public class Shower implements Device 
{
	
	String name;
    boolean isOn;
     long totalTimeInCurrentState;
	
     public Shower(String name) 
     {
         this.name = name;
     }

     @Override
     public String getName() 
     {
         return name;
     }

     @Override
     public boolean isOn()
     {
         return isOn;
     }

     @Override
     public void turnOn() 
     {
         isOn = true;
         
         totalTimeInCurrentState -= System.currentTimeMillis();
     }

     @Override
     public long getTotalTimeInCurrentState() 
     {
         return totalTimeInCurrentState;
     }

	@Override
	public void turnOff()
	{
		isOn = false;
        
        totalTimeInCurrentState += System.currentTimeMillis();
		
	}
 
	

}

public class Television extends Electronicdevice
{

	public Television(String name) 
	{
		super(name);
		// TODO Auto-generated constructor stub
	}

	
	@Override
    public String getName() 
    {
        return name;
    }

    @Override
    public boolean isOn()
    {
        return isOn;
    }

    @Override
    public void turnOn() 
    {
        isOn = true;
        
        totalTimeInCurrentState += System.currentTimeMillis();
    }

    
    @Override
	public void turnOff() 
    {
    	isOn = false;
        
        totalTimeInCurrentState -= System.currentTimeMillis();
	}

	@Override
    public long getTotalTimeInCurrentState() 
    {
        return totalTimeInCurrentState;
    }
}

import java.util.HashMap;
import java.util.Map;

public class room extends House 
{

	int roomno;
	 String name;
	 private Map<String, Device> devices;
	  
	 public room(String name) 
	 {
	        this.name = name;
	        this.devices = new HashMap<>();
	 }

	  
		public void addDevice(Device device) 
	    {
	        devices.put(device.getName(), device);
	    }

	    public void turnOnDevice(String deviceName) 
	    {
	        Device device = devices.get(deviceName);
	        if (device != null) 
	        {
	            device.turnOn();
	        }
	    }

	    public void turnOffDevice(String deviceName) 
	    {
	        Device device = devices.get(deviceName);
	        if (device != null) 
	        {
	            device.turnOff();
	        }
	    }

	    public void displayStatus() 
	    {
	        System.out.println("Room: " + name);
	        for (Device device : devices.values()) 
	        {
	            System.out.println("   " + device.getName() + ": " + (device.isOn() ? "On" : "Off"));
	            System.out.println("      Total Time In Current State: " + device.getTotalTimeInCurrentState() + " ms");
	        }
	    }


}

import java.util.Scanner;

public class main 
{

	

	public static void main(String[] args) 
	{
		// TODO Auto-generated method stub

		Scanner sc=new Scanner (System.in);
		House house = new House(); 
		
		int choice = 0;
		while (choice != 8) 
        {
        	
            System.out.println("+-----------------------------------------------------------------------------+");
			System.out.println("|         |              //* Home Automation Menu *//                         |");
			System.out.println("|---------|-------------------------------------------------------------------|");
			System.out.println("|  1.     |           Add Room                                                |");
		    System.out.println("|  2.     |           Add Device to Room                                      |");
		    System.out.println("|  3.     |           Turn On Device in Room                                  |");
		    System.out.println("|  4.     |           Turn Off Device in Room                                 |");
		    System.out.println("|  5.     |           Display House Status                                    |");
		    System.out.println("|  6.     |           Display Room Status                                     |");
		    System.out.println("|  7.     |           List Total Time for Devices                             |");
		    System.out.println("|  8.     |           Exit                                                    |");
		    System.out.println("+---------|-------------------------------------------------------------------+");
            System.out.print("Enter your choice: ");

            choice = sc.nextInt();

            switch (choice) 
            {
                case 1:
                	
                	System.out.print("Enter Room Name: ");
                    String roomName = sc.next();
                    house.addRoom(roomName);
                    System.out.println("Room added successfully.");
                    break;

                case 2:
                    System.out.print("Enter Room Name: ");
                    String roomToAddDevice = sc.next();
                    room room = house.getRoom(roomToAddDevice);

                    if (room != null) 
                    {
                        System.out.print("Enter Device Name: ");
                        String deviceName = sc.next();
                        
                        room.addDevice(createDevice(deviceName));
                        System.out.println("Device added to the room successfully.");
                    } 
                    else 
                    {
                        System.out.println("Room not found.");
                    }
                    break;

                case 3:
                    System.out.print("Enter Room Name: ");
                    String roomToTurnOn = sc.next();
                    System.out.print("Enter Device Name: ");
                    String deviceToTurnOn = sc.next();
                    room roomToTurnOnObj = house.getRoom(roomToTurnOn);

                    if (roomToTurnOnObj != null) 
                    {
                        roomToTurnOnObj.turnOnDevice(deviceToTurnOn);
                        System.out.println("Device turned on successfully.");
                    } 
                    else 
                    {
                        System.out.println("Room not found.");
                    }
                    break;

                case 4:
                	System.out.print("Enter Room Name: ");
                    String roomToTurnOff = sc.next();
                    System.out.print("Enter Device Name: ");
                    String deviceToTurnOff = sc.next();
                    room roomToTurnOffObj = house.getRoom(roomToTurnOff);

                    if (roomToTurnOffObj != null) 
                    {
                        roomToTurnOffObj.turnOffDevice(deviceToTurnOff);
                        System.out.println("Device turned off successfully.");
                    } 
                    else 
                    {
                        System.out.println("Room not found.");
                    }
                    break;
                case 5:
                    house.displayStatus();
                    break;

                case 6:
                    System.out.print("Enter Room Name: ");
                    String roomToDisplayStatus = sc.next();
                    room roomToDisplayStatusObj = house.getRoom(roomToDisplayStatus);

                    if (roomToDisplayStatusObj != null) 
                    {
                        roomToDisplayStatusObj.displayStatus();
                    } 
                    else 
                    {
                        System.out.println("Room not found.");
                    }
                    break;

                case 7:
                   
                   house.totalTimeInCurrentState();
                    break;

                case 8:
                    System.out.println("Exiting Home Automation App. Goodbye!");
                    break;

                default:
                    System.out.println("Invalid choice. Please try again.");
                    break;
            }
        }

        sc.close();
    }

    
    private static Device createDevice(String deviceName) 
    {
       
        return new Electronicdevice(deviceName);
		
	}
        
	
}

	# JavaProject
