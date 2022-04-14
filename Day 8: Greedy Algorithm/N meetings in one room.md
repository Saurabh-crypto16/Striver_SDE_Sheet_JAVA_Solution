```java
// Comparator function which can compare 
// the ending time of the meeting ans 
// sort the list
class mycomparator implements Comparator<meeting>{
    @Override
    public int compare(meeting o1, meeting o2){
        if (o1.end < o2.end){
            // Return -1 if second object is
            // bigger then first
            return -1;
        }else if (o1.end > o2.end){
            // Return 1 if second object is
            // smaller then first
            return 1;
        }   
        return 0;
    }
}

// Custom class for storing starting time,  
// finishing time and position of meeting. 
class meeting{
    int start;
    int end;
    int pos;
    
    meeting(int start, int end, int pos){
        this.start = start;
        this.end = end;
        this.pos = pos;
    }
}

class Solution 
{
    //Function to find the maximum number of meetings that can
    //be performed in a meeting room.
    public static int maxMeetings(int start[], int end[], int n)
    {
        ArrayList<meeting> meet = new ArrayList<>();
        for(int i = 0; i < start.length; i++)
            meet.add(new meeting(start[i], end[i], i+1));
        
        // Initialising an arraylist for storing answer
        ArrayList<Integer> m = new ArrayList<>();
        
        int time_limit = 0;
        
        mycomparator mc = new mycomparator(); 
        
        // Sorting of meeting according to their finish time.
        Collections.sort(meet, mc);
        
        // Initially select first meeting. 
        m.add(meet.get(0).pos);
        
        // time_limit to check whether new meeting can be conducted or not. 
        time_limit = meet.get(0).end;
        
        // Check for all meeting whether it can be selected or not. 
        for(int i = 1; i < meet.size(); i++)
        {
            if (meet.get(i).start > time_limit)
            {
                
                // Add selected meeting to arraylist
                m.add(meet.get(i).pos);
                
                // Update time limit
                time_limit = meet.get(i).end;
            }
        }
        
        return m.size();
    }
}
```
