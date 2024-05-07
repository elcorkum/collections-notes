###  COLLECTIONS

A collection is a grouping of general Java objects
The Collection interface is a blueprint that provides the methods that an object must be able to implement to be a collection.

LISTS
Lists inherit from the Collection  interface.
A list is an ordered group of values indexed numerically.
A list is also an interface. It has its own interface specific methods that it can implement
List is abstract and cannot be instantiated
To instantiate we have to use a non-abstract implementation of a list such as:
Building our custom lists
ArrayList
LinkedList
Vector
Stack

ArrayList is the most commonly used.
```
public class Website{
    @Inject
    private List<String> urlList;
    //creating a list

    public Website() {
        urlList = new ArrayList<>();
        //initializing List as ArrayList
    }

    public void printURLs() {
    
    //adding String objects to list
        urlList.add("https://pluralsight.com/search?q=java");
        urlList.add("https://medium.com/search?q=java");
        urlList.add("https://stackoverflow.com/questions/tagged/java");
        urlList.add("https://stackoverflow.com/search?q=java+list");
        urlList.add("https://reddit.com/r/java");
        urlList.add("https://reddit.com/r/javahelp");
        
    //removing the object at index 1
        urlList.remove(1);
        
    //iterating through the list to print every objects in the list

        System.out.println("Links from stackoverflow.com:");
        for(String url: urlList){
                System.out.println(url);
        }
    }
    
```

Lists solve some of the pitfalls that arrays have.
An array has to have a set size with a specified number of objects where as a List can contain as many objects as we put in it.
If an array is initialized with a size of three, it can only ever hold three elements
If we tried to add a fourth element, we would get an _**ArrayIndexOutOfBoundsException**_
A List on the other hand can start with 0 objects in it and continue to grow as we add objects into it.

We can get part of a List using the subList() method.


###   MAPS
The map interface is an interface
A map is an unordered group of key-value pairs thar are indexed by a key.
Keys must be unique.
The map interface has 25 methods.
We need a non-abstract implementation of Map because it is an interface
We can use:
Custom Map
HashMap
TreeMap
LinkedHashMap

```
Map<String, Integer> coursesByLanguage = new HashMap<>();
    //Often we use a general Map for the type on the left (Map) instead of (HashMap)
    //Because of polymorphism we can later on change to a different implementation such as TreeMap
    //This affords us flexibility rather than limiting us to just oe type of Map.

    coursesByLanguage.put("Math", 1);
    //we add elements to the map using the put()
    //We have to put in the key-value pair as the parameter and these have to match the data types specified by the Map types

     coursesByLanguage.get("Math");
    //We get a value by accessing it through its corresponding key

     coursesByLanguage.containsKey("Math");
     //This code checks whether Math is in the map

      coursesByLanguage.keySet();
      //This returns a set of all the keys within the Map
```

Order of the key-value pairs in a Map depends on the type of Map

HashMap - here there is no guaranteed order

LinkedHashMap - Order according to insertion order

TreeMap - Ordered according to the alphanumeric order of the keys

```
//iterating through a Map using forEach loop


public void print() {

      for(Map.Entry<String, String> entry : dictionary.entrySet()){
        System.out.println(entry.getKey() + ": " + entry.getValue());
      }
```


###   SET
Set is an interface that inherits from the Collection interface
A set is group of unique values without an index where a list may contain non-unique values but every value has a unique index
Set is abstract and cannot be instantiated.
We can implement abstract implementations such as:

Custom
HashSet
TreeSet
EnumSet
Sets do not allow duplicates. If we try to add a value that already exists in the set, it will not be added
One of the benefits of sets is that we can compare the values in two different sets in two ways

intersection(retainAll)
union(addAll)

```
public void initalizeTitles() {
        javaTitles.add("Leveraging Java Data Structures");
        javaTitles.add("Java Lambdas: Getting Started");
        javaTitles.add("My First Spring Boot App");
        javaTitles.add("Spring Boot and React");

        webTitles.add("Creating the Same App with React and Angular");
        webTitles.add("Learn Kubernetes in Under 4 Hours");
        webTitles.add("My First Spring Boot App");
        webTitles.add("Spring Boot and React");

        Set<String> intersection = new HashSet<>(javaTitles);
        
        //the code below gets all the titles that are common in javaTitles and webTitles
        intersection.retainAll(webTitles);

        System.out.println(intersection);

    }
```

```
public void initalizeTitles() {
        javaTitles.add("Leveraging Java Data Structures");
        javaTitles.add("Java Lambdas: Getting Started");
        javaTitles.add("My First Spring Boot App");
        javaTitles.add("Spring Boot and React");

        webTitles.add("Creating the Same App with React and Angular");
        webTitles.add("Learn Kubernetes in Under 4 Hours");
        webTitles.add("My First Spring Boot App");
        webTitles.add("Spring Boot and React");

        Set<String> strictlyJavaSet = new HashSet<>(javaTitles);
        //the code below removes all the titles found in both javaTitles and webTitles
        strictlyJavaSet.removeAll(webTitles);
        
        //This code prints the remaining titles that are strictly javaTitles
        System.out.println(strictlyJavaSet);


    }
```
To sort a Set, we simply use the TreeSet implementation as it defaults to ordering the set in alphabetical order
We can easily combine two lists while ensuring no duplicate values using sets as opposed to using lists
We can also sort a collection of objects much easier by using a TreeSet than using lists.

```
public void initializeTitles() {
        javaTitles.add("Leveraging Java Data Structures");
        javaTitles.add("Java Lambdas: Getting Started");
        javaTitles.add("My First Spring Boot App");
        javaTitles.add("Spring Boot and React");

        webTitles.add("Creating the Same App with React and Angular");
        webTitles.add("Learn Kubernetes in Under 4 Hours");
        webTitles.add("My First Spring Boot App");
        webTitles.add("Spring Boot and React");

        Set<String> union = new TreeSet<>(javaTitles);
        
        //this code adds two sets together, while removing all duplicate values
        //the TreeSet automatically sorts the values in alphabetical order.
        union.addAll(webTitles);

        System.out.println(union);
    }
```




