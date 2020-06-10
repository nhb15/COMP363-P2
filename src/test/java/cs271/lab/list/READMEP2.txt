COMP 413 Project 2 Report

TestList.java and TestIterator.java

	TODO also try with a LinkedList - does it make any difference?

		It does not make a difference functionally. We are still able to add the values/nodes the same way. 
		It does not fix any of the errors on its own. 
		It still works because the list attribute is setup as a List so we can use either. 

TestList.java

	testRemoveObject()

		list.remove(5); // what does this method do?

			This method call will remove the index in the list as specified in the parameter. In this specific case, 
			it will remove the 5th index's value (the last 77) and move all remaining indices up one spot so that
			the list doesn't have an empty index. 

		list.remove(Integer.valueOf(5)); // what does this one do?

			This method call will remove the first value or object found in the list that matches the parameter. It starts searching
			from index 0, and if it finds a value or object that matches it will remove it and return true. Similar to above, it
			moves the indices after the target forward so that no void index exists.
			
			In this specific case. it removes the first value found of 5.  

TestIterator.java

	testRemove()

		i.remove(); // what happens if you use list.remove(77)?

			If we use list.remove(Integer.valueOf(77)), we must alter the loop in some way otherwise it will be
			an infinite loop, since i is not iterating. 

			One way we could solve this is by changing the loop header/condition to use: 
			while (list.contains(Integer.valueOf(77))). 

			This method is slightly different in functionality since we're removing the value of 77 in the list
			each loop as opposed to having the index in hand and removing it if it is 77. 

TestPerformance.java

	State how many times the tests were executed for each SIZE (10, 100, 1000 and 10000)
	to get the running time in milliseconds and how the test running times were recorded.

	SIZE 10
				 #1   #2   #3  
        testArrayListAddRemove:  21ms 20ms 18ms 
        testLinkedListAddRemove: 20ms 19ms 21ms 
	testArrayListAccess:     9ms  11ms 8ms 
        testLinkedListAccess:    8ms  9ms  7ms 

	SIZE 100
				 #1   #2   #3  
        testArrayListAddRemove:  32ms 30ms 30ms
        testLinkedListAddRemove: 27ms 20ms 23ms
	testArrayListAccess:     12ms 9ms  20ms 
        testLinkedListAccess:    25ms 19ms 21ms 

	SIZE 1000
				 #1    #2    #3   
        testArrayListAddRemove:  113ms 111ms 118ms 
        testLinkedListAddRemove: 27ms  28ms  19ms
	testArrayListAccess:     13ms  13ms  11ms 
        testLinkedListAccess:    299ms 291ms 309ms

	SIZE 10000
				 #1     #2     #3   
        testArrayListAddRemove:  1128ms 1114ms 1176ms 
        testLinkedListAddRemove: 21ms   22ms   22ms
	testArrayListAccess:     13ms   13ms   12ms
        testLinkedListAccess:    3918ms 3889ms 3701ms

	listAccess - which type of List is better to use, and why?

		ArrayList is clearly better in accessing information at size 1000 and above. Therefore, ArrayList is better. 
		This is because array lists can access instantly by using the index of the desired target. So highly increased sizes
		do nothing to prevent high performance. 

	listAddRemove - which type of List is better to use, and why?

		LinkedList is clearly better in add/remove functionality at size 1000 and above. Therefore, LinkedList is better. 
		This is because linked lists can easily remove a node at any point in the list, rearrange the pointers, and not worry about indeces. 
		In array lists, if element 25 gets removed in a 1000 element list, we still need to work with ~1000 elements as opposed to ~3 in a linked list. 

	REPS observations: 
		
		Changing REPS increases ms across the board in non-linear fashion. 