# sorting_earthquake_data
Program to use various sorting methods on data from earthquakes. 

## Implementing Selection Sort

* The class Location, from the Android platform (slightly revised for our purposes), a data class representing a geographic location. One of the constructors has parameters latitude and longitude, and one of the public methods is distanceTo.

* The class QuakeEntry, from the lesson, which has a constructor that requires latitude, longitude, magnitude, title, and depth. It has several get methods and a toString method.

* The class EarthQuakeParser, from the lesson, which has a read method with one String parameter that represents an XML earthquake data file and returns an ArrayList of QuakeEntry objects.

* The QuakeSortWithTwoArrayLists class sorts by magnitude, using two ArrayLists of QuakeEntry’s. 

>* sortByMagnitude calls the getSmallestMagnitude function which returns the smallest magnitude in the 'in' arraylist. It then removes the entry from the 'in' arraylist and adds it to the 'out' arraylist, repeating until all entries in the 'in' arraylist are exhausted and the 'out' arraylist is filled (and sorted). 

>* getSmallestMagnitude takes in an arraylist, comparing all elements against the smallest value and updating as a newer minimum value is find. After finishing all iterations, returns the smallest value. 
------pickup here------
* The QuakeSortInPlace class is the class you will modify. Currently it implements the selection sort algorithm that sorts earthquakes by magnitude in place, in one ArrayList of QuakeEntry’s. The code for the method sortByMagnitude was shown in the video “In Place.” You should run the testSort method and understand how this sorting algorithm works. 
