# <pre>                  IT314 - Software Engineering </pre>

#### Name       : Bhatt Meet Dhavalbhai
#### Student ID  : 202001267
#### Lab        : 8

----

## Objective:
    The goal of this lab is to learn how to use JUnit to write unit tests for Java programs.

----
1. Creating eclipse project named <b>Lab8</b> and a package named <b>myPackage</b> inside src folder in it.

![image](https://user-images.githubusercontent.com/77287821/233029175-367810f4-956d-4a8a-ac9f-5209d9547f90.png)

2. Creating a class for a Boa with the given code snippet in the lab manual.
```
public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;
	
	public Boa (String name, int length, String favoriteFood){
  
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
    
	}
	
	//returns true if this Boa constructor is healthy
	public boolean isHealthy(){
  
		return this.favoriteFood.equals("granola bars");
    
	}
	
	//returns true if the length of this Boa constructor is
	//less than the given cage length
	public boolean fitsInCage(int cageLength){
  
		return this.length < cageLength;
    
	}
  
  
}	
```
![image](https://user-images.githubusercontent.com/77287821/233030808-22d5c9ee-5336-4a22-b503-c97158144143.png)

3. Creating JUnit test file named <b>BoaTest</b>.  

![image](https://user-images.githubusercontent.com/77287821/233030951-9f13aac1-a60b-4216-b357-a9147e9707f1.png)

4. Initializing ken and jen as private Boa's.
```
import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
  private Boa ken;
	
	@Before
	public void setUp() throws Exception {
    // initialization
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa("Kenneth", 3, "granola bars");
	}
}
```

5. Implementing test cases for **isHealthy()** and **fitsInCage()** functions.
```
import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
  private Boa ken;
	
	@Before
	public void setUp() throws Exception {
    // initialization
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa("Kenneth", 3, "granola bars");
	}

	@Test
	public void testIsHealthy() {
		// testing isHealthy for two objects
		assertEquals(false,jen.isHealthy());
    
    assertEquals(true,ken.isHealthy());
	}
	
	@Test
	public void testFitsInCage() 
  {
    
    assertEquals(false,jen.fitsInCage(1)); // less than cage size
    
    assertEquals(false,jen.fitsInCage(2)); // equal to cage size
    
    assertEquals(true,jen.fitsInCage(3)); / greater than cage size
    
	}
  
}
```
![image](https://user-images.githubusercontent.com/77287821/233031388-2d7ed35f-0fef-4c43-8c3d-75ab98c73559.png)
For testing the fitsInCage() function, there is no need to write tests for both jen and ken objects as the function is same for both and the output of test cases depends only whether the given lenght is greater than,less than or equal to actual length of object.The behaviour will be similar in both cases.

6. Running the tes cases. All test cases are passed and there is no red bars in the output. Both 2 test cases are passed.

![image](https://user-images.githubusercontent.com/77287821/233036803-be8c0390-ef86-4d73-9277-4e85555f43bd.png)

7. Adding a new method to the Boa class with name <b>lenghtInInches()</b> to get the length in inches.
```
//returns the length of the Boa in inches
public int lenghtInInches() {
  int LengthInches = this.length * 12;
  
  return LengthInches;
  
}
```
![image](https://user-images.githubusercontent.com/77287821/233037826-f7459d32-e1ca-4a32-98b3-5d99617ddfc6.png)
As the length of the Boa is given in feet, to convert it into inches, We simply multiply length with 12 and return the value.

8. Adding another test case and running all 3 test cases together.
```
@Test
public void teslengthInInches() {
  assertEquals(24, jen.lenghtInInches());
  assertEquals(36, ken.lenghtInInches());
}
```
![image](https://user-images.githubusercontent.com/77287821/233038501-4963e088-a680-4d34-a138-b7264e6ddbde.png)
As a result, test cases have been created for the specified Boa class, and the necessary Junit test cases have been used to test all three methods.
