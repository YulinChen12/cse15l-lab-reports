Array Methods

I'll provide an example of a bug from week 4's lab and follow the requested format for a failure-inducing input, a non-failure-inducing input, symptoms, bug, and a code change to fix the issue. 

I'll consider a bug in a hypothetical Java program where a method to calculate the average of an array of integers, `averageWithoutLowest`, has a bug. The bug is that it does not correctly exclude the lowest element when calculating the average.

Failure-Inducing Input:

JUnit Test for the Bug:
```java
@Test
public void testReverseInPlace_Bug() {
    int[] inputArray = {1, 2, 3, 4, 5};
    ArrayExamples.reverseInPlace(inputArray);
    assertArrayEquals(new int[]{5, 4, 3, 2, 1}, inputArray);
}
```

JUnit Test for the no Bug:
```java
@Test
public void testReverseInPlace_no_Bug() {
    int[] inputArray = {1};
    ArrayExamples.reverseInPlace(inputArray);
    assertArrayEquals(new int[]{1}, inputArray);
}
```
Symptom:

With bug:

![Image](bug2.png)

No bug:
![Image](bug.png)

Fix the bug:

The code before with the bug is 

```java
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

The correct code should be:
```java
static void reverseInPlace(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[n - i - 1];
        arr[n - i - 1] = temp;
    }
}
```

Explanation:

The old code attempted to reverse the input array in place but had a logical error in the loop. The problem was that it overwrote the values in the original array with reversed values incorrectly.

But the new code:
It introduces a variable n to store the length of the array, which simplifies the code and avoids recomputing the length in each iteration.

It uses a for loop to iterate from the beginning of the array to halfway. This is because when you swap the first half of the array with the second half, you effectively reverse the entire array.

Inside the loop, it uses a temporary variable temp to store the value at the current index i. This is necessary to ensure that values aren't lost during the swapping process.

It swaps the value at index i with the corresponding value at index n - i - 1, effectively reversing the values in the array.



Part2:

I will work with the grep command. I will show you 4 variations and alternate ways to use this command.
```java
grep -r -1
```

Analternative way to find the file that contains the string “fall had been” in the data directory is to use grep -r -l "fall had been" .

```
[user@sahara ~/docsearch/technical/911report]$ grep -r -1 "fall had been"
chapter-9.txt-                institution, was in possession of the knowledge that the South Tower had collapsed
chapter-9.txt:                as early as the NYPD, as its fall had been immediately reported by an FDNY boat on a
chapter-9.txt-                dispatch channel. Because of internal breakdowns within the department, however,
```

The -r flag is used to look through all of the subdirectories to find a specific pattern. The -l flag is used to print the names of the files
where the pattern (in our case “fall had been”) is found. Combining them returns the path to all files where the string “fall had been” is. (in our
case it’s chapter-9.txt).

```
[user@sahara ~/docsearch/technical/911report]$ grep -r  "fall had been"
chapter-9.txt:                as early as the NYPD, as its fall had been immediately reported by an FDNY boat on a
```
Or, for example, the pattern “as its fall had been” can be found in these files.

```
grep - n
```

```
[user@sahara ~/docsearch/technical/911report]$ grep -n "report" chapter-9.txt
122:                designated "transition team"- reported to their regular stations to provide
296:                groups, primarily between the 103rd and 106th floors. A large group was reported on
311:                advised by the Port Authority fire safety director-who had reported to the lobby
371:                debilitating volumes and isolated fires were reported, although there were some
466:                zone as scouting units and reporting back to the chiefs in the lobby. The radio
479:                to report back on conditions, but did not know what the impact floors were; they did
516:                specific casualty reports. In addition, many ambulance paramedics from private
520:            Numerous NYPD officers saw the plane strike the North Tower and immediately reported
535:                report on conditions and assess the feasibility of a rooftop landing or of special
691:                location on the 100th floor, and severe smoke conditions were reported throughout
695:                reports of tremendous smoke on that floor, but at least one area remained less
743:                tower, and stairwell A was reported to have been almost empty. Stairwell B was also
744:                reported to have contained only a handful of descending civilians at an earlier
756:                least one stairwell was reported to have been "clear and bright" from the upper 80s
811:                administrative positions-who lacked a predetermined operating role also reported to
849:                reports of what was seen from the [NYPD] helicopters. It was impossible to know how
862:            Many units were simply instructed to ascend toward the impact zone and report back to
900:                either because of a false report of a third plane approaching or because of his
956:                that had been dispatched to the North Tower prior to 9:03 reported immediately to
1000:                stairwell A; he reported that it looked open to the 79th floor, well into the impact
1001:                zone. He also reported numerous civilian fatalities in the area.
1014:                that 100 people were reported via 911 to be trapped on the 105th floor of the North
1015:                Tower, and Field Comm then attempted to convey that report to chiefs at the outdoor
1018:                because many units reported directly to the North Tower, the South Tower, or the
1044:                Chief of Department a status report and confirmed that this was a rescue, not
1146:            At 9:37, a civilian on the 106th floor of the South Tower reported to a 911 operator
1168:                police desk reporting at least 100 people trapped.
1373:                complex and nearby areas should be evacuated. At 10:04, NYPD aviation reported that
1387:                complex. This officer, who had observed the South Tower collapse, reported it to ESU
1398:                the descent, they reported seeing many firefighters who were resting and did not
1399:                seem to be in the process of evacuating. They further reported advising these
1404:                instruction from a cop that morning. However, another firefighter reports that ESU
1538:                This was the first of three evacuations caused by reports of incoming aircraft, and
1554:                communications, the report concludes: "Almost all aspects of communications continue
1756:                reporting from the tunnel and airport commands could not hear instructions being
1770:                reported to the same ESU command post. It is unclear, however, whether non-ESU NYPD
1804:                as early as the NYPD, as its fall had been immediately reported by an FDNY boat on a
```


This grep command with the -n flag not only finds the occurence of a pattern in a given file, but also prints the line where this pattern is.


```
[user@sahara ~/docsearch/technical/911report]$ grep -n "fall" chapter-9.txt
486:                some civilians on upper floors were jumping or falling from the building. They also
567:                could walk to vacate the area immediately. Putting themselves in danger of falling
782:                to the north and east so that they might avoid falling debris and victims.
790:                approaching lower floors. Other evacuees were killed earlier by debris falling on
1117:                endangered by falling debris and people on West Street, on the plaza between the
1258:                repeating"Mayday, Mayday, Mayday"-during the 29 minutes between the fall of the
1317:                leave, as this tower could fall as well. The units then proceeded to exit onto West
1443:                and avoid being struck by people and debris falling from the upper floors.
1794:                appeared to be about to fall and could pose a danger to those below. Immediately
1801:                the fall of either tower before the South Tower collapsed, and no NYPD personnel
1804:                as early as the NYPD, as its fall had been immediately reported by an FDNY boat on a
1829:                post. In our judgment, this falls short of an optimal response plan, which requires
```


We can use this command to search for a pattern in all text of a given directory.

```
grep - w
```
```
[user@sahara ~/docsearch/technical/911report]$ grep -w "fall" chapter-9.txt
                repeating"Mayday, Mayday, Mayday"-during the 29 minutes between the fall of the
                leave, as this tower could fall as well. The units then proceeded to exit onto West
                appeared to be about to fall and could pose a danger to those below. Immediately
                the fall of either tower before the South Tower collapsed, and no NYPD personnel
                as early as the NYPD, as its fall had been immediately reported by an FDNY boat on a
```


This grep command variation with a -w flag finds the actual pattern (in our case “fall”) instead of finding also the modifications of this
word. For example, the $ grep -n "fall" chapter-9.txt command would print lines that contain words fall as well.


```
[user@sahara ~/docsearch/technical/911report]$ grep -r -1 -w "fall" chapter-9.txt
                building's collapse may be imminent-a protocol that includes constantly
                repeating"Mayday, Mayday, Mayday"-during the 29 minutes between the fall of the
                SouthTower and that of the NorthTower. In addition, most of the evacuation
--
                earlier seen from a window that the SouthTower had collapsed-urged that they all
                leave, as this tower could fall as well. The units then proceeded to exit onto West
                Street. While they were doing so, the NorthTower began its pancake collapse, killing
--
                At 9:51 A.M., a helicopter pilot cautioned that "large pieces" of the South Tower
                appeared to be about to fall and could pose a danger to those below. Immediately
                after the tower's collapse, a helicopter pilot radioed that news. This transmission
--
                be overstated. Contrary to a widely held misperception, no NYPD helicopter predicted
                the fall of either tower before the South Tower collapsed, and no NYPD personnel
                began to evacuate the WTC complex prior to that time. Furthermore, the FDNY, as an
                institution, was in possession of the knowledge that the South Tower had collapsed
                as early as the NYPD, as its fall had been immediately reported by an FDNY boat on a
                dispatch channel. Because of internal breakdowns within the department, however,
```


The flags -r , -l , -w and many others can be combined. For example, in this case the output is the paths to all .txt files in all the
subdirectories that contain the pattern “fall” and only “fall”.

```
grep -c 
```

![Image](grep-c1.png)


Here, the -c flag prints how many occurences of a pattern (in our case “fall”) is in chapter-9.txt and the paths to the files. 

![Image](grep-c2.png)

Here, we are trying to find the pattern “report” in chapter-9.txt files As we can see there is 37
occurrence of “report” in the txt file
