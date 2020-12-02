# sorting_earthquake_data
Program to use various sorting methods on data from earthquakes. 

## Implementing Selection Sort and Bubble Sort

<b>Location</b> - a data class from the Android platform (slightly revised for our purposes), a data class representing a geographic location. One of the constructors has parameters latitude and longitude, and one of the public methods is distanceTo.

<b>QuakeEntry</b> - a class which has a constructor that requires latitude, longitude, magnitude, title, and depth. It has several get methods and a toString method.

<b>EarthQuakeParser</b> - a class which has a read method with one String parameter that represents an XML earthquake data file and returns an ArrayList of QuakeEntry objects.

<b>QuakeSortWithTwoArrayLists</b> - a class which sorts by magnitude, using two ArrayLists of QuakeEntry’s. 
* *sortByMagnitude* - calls the *getSmallestMagnitude* function which returns the smallest magnitude in the 'in' arraylist. It then removes the entry from the 'in' arraylist and adds it to the 'out' arraylist, repeating until all entries in the 'in' arraylist are exhausted and the 'out' arraylist is filled (and sorted). 

* *getSmallestMagnitude* - takes in an arraylist, comparing all elements against the smallest value and updating as a newer minimum value is found. After finishing all iterations, returns the smallest value. 

<b>QuakeSortInPlace</b> - a class which implements the selection sort algorithm that sorts earthquakes by magnitude in place, in one ArrayList of QuakeEntry’s. Contains the following methods:
* *sortByMagnitude* - calls the *getSmallestMagnitude* function which returns the smallest magnitude in the 'in' arraylist. It then removes the entry from the 'in' arraylist and adds it to the 'out' arraylist, repeating until all entries in the 'in' arraylist are exhausted and the 'out' arraylist is filled (and sorted). 
* *getSmallestMagnitude - takes in an arraylist, comparing all elements against the smallest value and updating as a newer minimum value is found. After finishing all iterations, returns the smallest value. 
* *sortByLargestDepth* -  has one parameter, an ArrayList of type QuakeEntry named in. This method sorts the QuakeEntry’s in the ArrayList by depth using the selection sort algorithm, but in reverse order from largest depth to smallest depth (the QuakeEntry with the largest depth should be in the 0th position in the ArrayList). This method calls the method *getLargestDepth* repeatedly until the ArrayList is sorted. 
* *getLargestDepth* - has two parameters, an ArrayList of type QuakeEntry named quakeData and an int named from representing an index position in the ArrayList. This method returns an integer representing the index position of the QuakeEntry with the largest depth considering only those QuakeEntry’s from position from to the end of the ArrayList. 
* *onePassBubbleSort* - has two parameters, an ArrayList of type QuakeEntry named quakeData and an int named numSorted that represents the number of times this method has already been called on this ArrayList and thus also represents the number of the elements that are guaranteed to already be where they belong when the ArrayList is sorted by magnitude. This method makes one pass of bubble sort on the ArrayList. It takes advantage of the fact that the last numSorted elements are already in sorted order.
* *sortByMagnitudeWithBubbleSort* - has one parameter, an ArrayList of type QuakeEntry named in. If the ArrayList in has N elements in it, this method calls onePassBubbleSort N – 1 times to sort the elements in in.
* *checkInSortedOrder* - has one parameter, an ArrayList of type QuakeEntry named quakes. This method returns true if the earthquakes are in sorted order by magnitude from smallest to largest. Otherwise this methods returns false. 
* *sortByMagnitudeWithBubbleSortWithCheck* - has one parameter, an ArrayList of type QuakeEntry named in. If the ArrayList in has N elements in it, this method calls onePassBubbleSort at most N – 1 times.  This method should call *checkInSortedOrder* and stop early if the ArrayList is already sorted. This method prints how many passes were needed to sort the element.
* *sortByMagnitudeWithCheck* - has one parameter, an ArrayList of type QuakeEntry named in. This method sorts earthquakes by their magnitude from smallest to largest using selection sort similar to the sortByMagnitude method. However, this method calls *checkInSortedOrder* and stops early if the ArrayList is already sorted. This method prints how many passes were needed to sort the elements. For selection sort, one pass has exactly one swap. 
* *testSort* - method used to test the methods above.

Link to exercise: https://www.coursera.org/learn/java-programming-design-principles/supplement/fA6FH/programming-exercise-implementing-selection-sort

## Sorting at Scale (EfficientSortStarterProgram)

<b>Location</b>, <b>QuakeEntry</b> and <b>EarthQuakeParser</b> - classes reused (see above) *compareTo* in the QuakeEntry class is modified for this program so it should now sort quake by magnitude first, from smallest magnitude to largest magnitude, and then break ties.

<b>DifferentSorters</b> - a class which includes several methods to test several of the classes/methods used.
* *sortByLastWordInTitleThenByMagnitude* - this method creates an EarthQuakeParser, reads data from a file on earthquakes and creates an ArrayList of QuakeEntry’s. Then this method calls Collections.sort on this ArrayList and uses the TitleLastAndMagnitudeComparator to sort the earthquakes. You should be able to see that the earthquakes are sorted by the last word in their title, and those with the same last word are sorted by magnitude. 
* *sortByTitleAndDepth* - creates an EarthQuakeParser, reads data from a file on earthquakes and creates an ArrayList of QuakeEntry’s. Then calls Collections.sort on this ArrayList and use the *TitleAndDepthComparator* to sort the earthquakes. Earthquakes are sorted by title first, and those with the same title are sorted by depth. 
* *sortWithCompareTo* - sorts earthquake data using the *compareTo* method. The earthquakes are sorted by magnitude, and those with the same magnitude are sorted by depth.
* *sortByMagnitude* - helper method which uses Collections.sort to sort the earthquakes by magnitude. 
* *sortByDistance* - helper method which uses Collections.sort to sort the earthquakes by distance.


<b>DistanceComparator</b> - a class which implements Comparator to allow one to sort QuakeEntry’s by their distance to a specified location that is passed in as a parameter.

<b>MagnitudeComparator</b> - a class which implements Comparator to allow one to sort QuakeEntry’s by magnitude from smallest to largest magnitude. 

<b>TitleAndDepthComparator</b> - a class which implements a Comparator of type QuakeEntry. Contains the the *compare* method.
* *compare* - a method that has two parameters, a QuakeEntry named q1 and a QuakeEntry named q2. This method compares the title of q1 and q2. If q1’s title comes before q2’s title in alphabetical order, then this method returns a negative integer. If q1’s title comes after q2’s title, then this method returns a positive integer. If q1’s title is the same as q2’s title, then this method compares the depth of the two earthquakes. If q1’s depth is less than q2’s depth, then this method returns a negative number. If q1’s depth is greater than q2’s depth, then this method returns a positive integer. Otherwise, this method returns 0. 

<b>TitleLastAndMagnitudeComparator</b> - a class which implements a Comparator of type QuakeEntry. Contains the *compare* method. 
* *compare* - a method that has two parameters, a QuakeEntry named q1 and a QuakeEntry named q2. The method compares the last word in the title of q1 and q2. If q1’s last word comes before q2’s last word in alphabetical order, then this method returns a negative integer. If q1’s last word comes after q2’s last word, then this method returns a positive integer. If q1’s last word is the same as q2’s last word, then this method compares the magnitude of the two earthquakes. If q1’s magnitude is less than q2’s magnitude, then this method returns a negative number. If q1’s magnitude is greater than q2’s magnitude, then this method returns a positive integer. Otherwise, this method returns 0. 

Link to exercise: https://www.coursera.org/learn/java-programming-design-principles/supplement/OnNGh/programming-exercise-sorting-at-scale
