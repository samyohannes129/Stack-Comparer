# Stack-Comparer
Program creates 2 stacks and determines whether they are are identical or not 
/**
 * Description: Program creates 2 stacks and determines whether they are are identical or not
 * 
 * Input: 2 stacks
 * 
 * Output: Whether stacks are equal or not
 * 
 * @author Samuel Yohannes
 * @contact mi8854we@go.minnstate.edu
 * @since 10/25/23
 * 
 * Institution: Century College
 *  Professor: Matthew Nyamagwa
 * 
 */
import java.util.EmptyStackException;
public class driver {
	public static void main(String[] args) {
		
		//Creates 2 new stacks
		IntLinkedStack intStack1 = new IntLinkedStack();
		IntLinkedStack intStack2 = new IntLinkedStack();
		int[] array = {21, 14, 19, 43, 58, 78, 77, 93, 95, 58};

		
		//PUSHES array into stack
		for(int i = 0; i < array.length; i++)
			intStack1.push(array[i]);
		for(int i = 0; i < array.length; i++)
			intStack2.push(array[i]);
		
		// try and catch block to catch exceptions while popping nodes in stack 1
		try {
		System.out.println("Popped: " + intStack1.pop());
		//Popping twice
		System.out.println("Popped: " + intStack1.pop());
		} catch(EmptyStackException ex) {
			System.out.println(ex);
		}catch (ArrayIndexOutOfBoundsException ex) {
			System.out.println(ex);
		}catch (Exception ex) {
			System.out.println(ex);
		}
		
		//pushing vlaues and printing them with the size
		intStack1.push(99);
		intStack1.push(999);
		System.out.println("Stack: " + intStack1.toString(intStack1));
		System.out.println("Size: " + intStack1.size());
		
		// try and catch block to catch exceptions while popping nodes in stack 2
		try {
		System.out.println("Popped: " + intStack2.pop());
		System.out.println("Popped: " + intStack2.pop());
		} catch(EmptyStackException ex) {
			System.out.println(ex);
		}catch (ArrayIndexOutOfBoundsException ex) {
			System.out.println(ex);
		}catch (Exception ex) {
			System.out.println(ex);
		}
		
		//pushing values and printing them with the size
		intStack2.push(99);
		intStack2.push(999);
		System.out.println("Stack: " + intStack2.toString(intStack2));
		System.out.println("Size: " + intStack2.size());
		
		//outputs whether the stacks are identical or not
		System.out.println("Stacks are identical: " + compareStacks(intStack1, intStack2));
    
	}

	/**
	 * 
	 * Compares if Stacks are identical or not
	 * @param LinkedStack stack1
	 * @param LinkedStack stack2
	 * @return true or false
	 */
	private static boolean compareStacks(IntLinkedStack stack1, IntLinkedStack stack2) {
	        if (stack1.size() != stack2.size()) {
	            return false;
	        }
	        while (!stack1.isEmpty()) {
	            if (stack1.pop()!=stack2.pop()) {
	                return false;
	            }
	        }
		return true;
	}
}

/**
 * Description: Program implements LinkedStackInterface and creates getters and setters for the properties
 * 
 * @author Samuel Yohannes
 * @contact mi8854we@go.minnstate.edu
 * @since 10/25/23
 * 
 * Institution: Century College
 *  Professor: Matthew Nyamagwa
 * 
 */
import java.util.EmptyStackException;
public class IntLinkedStack implements LinkedStackInterface {
	
	//PROPERTIES
	private IntNode top;
	
	// CONSTRUCTOR
	
	//NO ARGUMENT CONSTRUCTOR
	/**
	 * Set initial array capacity to 10.
	 */
	public IntLinkedStack() {
		this.top = null;
	}

	
	@Override
	/**
	 * Gets Size of the Stack
	 */
	public int size() {
		return IntNode.listLength(this.top);
	}

	@Override
	/**
	 * Remove element from top of the stack
	 */
	public int pop() {
		if(isEmpty())
			throw new EmptyStackException();
		int data = this.top.getData();
		this.top = top.getLink();
		return data;
	}

	@Override
	/**
	 * add an element from the top of the stack
	 */
	public void push(int element) {
		this.top = new IntNode(element, top);
		
	}

	@Override
	/**
	 * Checks element at the top without removing 
	 * @return data
	 */
	public int peek() {
		if(isEmpty())
			throw new EmptyStackException();
		int data = this.top.getData();
		return data;
	}

	@Override
	/**
	 * Checks whether the stack is empty or not
	 */
	public boolean isEmpty() {
		// TODO Auto-generated method stub
		return this.top==null;
	}


	/**
	 * Returns visual representation of stack
	 */
	public String toString(IntLinkedStack head) {
		IntNode cursor;
		
		String list = "Head --> | ";
		for(cursor = this.top; cursor != null; cursor = cursor.link ) {
			list = list + cursor.getData() + " | --> | ";
		}
		list = list + "NULL";
		
		return list;
	}


}
/**
 * Description: Interface that imports properties to be used as getters and setters
 * 
 * @author Samuel Yohannes
 * @contact mi8854we@go.minnstate.edu
 * @since 10/25/23
 * 
 * Institution: Century College
 *  Professor: Matthew Nyamagwa
 * 
 */
public interface LinkedStackInterface {
	public int size();
	public int pop();
	public void push(int element);
	public int peek();
	public boolean isEmpty();

}




