# Dragonkiller
This program was coded in Netbeans using Java.

The program will prompt the user to enter their name and surname with a space in between, it will then run and output the following:
Your name and surname with the space removed,
an unsorted array list of numbers,
it will then sort that afore mentioned list,
it will then ask the user to choose a number fom the now sorted list which will be removed,
then it will replace the choisen number with a zero.

Here below is the code with comments:

import java.util.*;


/**
 *
 * @author Lenovo
 */
public class DragonKiller {

    /**
     * @param args the command line arguments
     */
    
 

     // This method remove space b/w name and surname
    static int RemoveSpace(String name)
    {
        String name_Surname;
        int count =0;
        //Remove all space
        name_Surname = name.replaceAll("\\s","");
        //Print the Name without space
        System.out.println("Name without Spaces is: " + name_Surname);
        for(int i = 0; i < name_Surname.length(); i++) 
        {    
                count++;    
        }   
        return count;
    }
    //Insert Sorting method
    static void inserting_Sort(int s_arr[]) {  
        int n = s_arr.length;  
        for (int j = 1; j < n; j++) {  
            int key_S = s_arr[j];  
            int i = j-1;  
            while ( (i > -1) && ( s_arr [i] > key_S ) ) {  
                s_arr [i+1] = s_arr [i];  
                i--;  
            }  
            s_arr[i+1] = key_S;  
        }  
    }  
    //Binary Search method
    static int binary_Search(int array[], int first_S, int last_S, int key_S)
    {  
        int midd = (first_S + last_S)/2;  
        while( first_S <= last_S )
        {  
            if ( array[midd] < key_S )
            {  
                first_S = midd + 1;     
            }
            else if ( array[midd] == key_S )
            {  
                System.out.println("Element is found at index: " + midd);  
                break;
            }
            else
            {  
                last_S = midd - 1;  
            }  
            
            midd = (first_S + last_S)/2;  
        }
        if ( first_S > last_S )
        {  
            midd = -1;
        }  
        return midd;
    } 
    public static void main(String[] args) {
        // TODO code application logic here
     
        
         String Name;        
        int[] arr_Dragon;  
        int size, min = 10, max = 50, element, index, killed_Element =0;
       Scanner Keyboard = new Scanner(System.in) ;
        System.out.println("Please enter your Name and Surname with a space in between.");
        Name = Keyboard.nextLine();
        System.out.println("The Original Name is: " + Name);
        size = RemoveSpace(Name);
        arr_Dragon = new int[size];
        for(int i = 0; i < arr_Dragon.length; i++)
        {
            int random = (int)(Math.random()*((max-min)+1))+min;
            if(random%2!=0)
            {
                arr_Dragon[i] = random;      
            }
            else
            {
                i = i-1;
            }
            
        }
        System.out.println("Elements of the array before insertion sort: ");
        for(int i = 0; i < arr_Dragon.length; i++)
        {
            System.out.print(arr_Dragon[i] + " ");
        }
        System.out.println();
        inserting_Sort(arr_Dragon);   
        System.out.println("Elements of the array after insertion sort: ");
        for(int i = 0; i < arr_Dragon.length; i++)
        {
            System.out.print(arr_Dragon[i] + " ");
        }
        System.out.println();
        System.out.println("Enter the element to search for and be remover(Killed).");
        element = Keyboard.nextInt();
        int last_S = arr_Dragon.length-1;
        index = binary_Search(arr_Dragon,0,last_S,element); 
        if(index == -1)
        {
            System.out.println("Element is not found!!!"); 
        }
        else
        {
            killed_Element = arr_Dragon[index];
            arr_Dragon[index] = 0;
        }
        System.out.println("Elements After Killing the Element: ");
        for(int i=0;i<arr_Dragon.length;i++)
        {
            System.out.print(arr_Dragon[i] + " ");
        }
        System.out.println();
        if(killed_Element != 0)
        {
            System.out.println("Element to be Killed is " + killed_Element);
        }
        else
        {
            System.out.println("No Element is Killed as No Element is found in the Array ");
        }

        
        
    }
    
}
