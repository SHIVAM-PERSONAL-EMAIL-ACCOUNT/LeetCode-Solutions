### Solution

```java
class UndergroundSystem {

    static class StationCheckIn {
        String stationName;
        int checkInTime;
        
        public StationCheckIn(String stationName, int checkInTime) {
            this.stationName = stationName;
            this.checkInTime = checkInTime;
        }
    }
    
    static class AverageTime {
        int observations;
        int total;
        
        public AverageTime() {
            observations = 0;
            total = 0;
        }
    }
    
    Map<Integer, StationCheckIn> checkInMap;
    Map<String, Map<String, AverageTime>> averageTimeMap;
    
    public UndergroundSystem() {
        checkInMap = new HashMap<>();
        averageTimeMap = new HashMap<>();
    }
    
    public void checkIn(int id, String stationName, int t) {
        checkInMap.put(id, new StationCheckIn(stationName, t));
    }
    
    public void checkOut(int id, String stationName, int t) {
        StationCheckIn checkIn = checkInMap.get(id);
        int time = t - checkIn.checkInTime;
        averageTimeMap.putIfAbsent(checkIn.stationName, new HashMap<>());
        Map<String, AverageTime> destinations = averageTimeMap.get(checkIn.stationName);
        destinations.putIfAbsent(stationName, new AverageTime());
        AverageTime destinationAverage = destinations.get(stationName);
        destinationAverage.total += time;
        destinationAverage.observations++;
    }
    
    public double getAverageTime(String startStation, String endStation) {
        AverageTime avgTime = averageTimeMap.get(startStation).get(endStation);
        return (double) avgTime.total / avgTime.observations;
    }
}

/**
 * Your UndergroundSystem object will be instantiated and called as such:
 * UndergroundSystem obj = new UndergroundSystem();
 * obj.checkIn(id,stationName,t);
 * obj.checkOut(id,stationName,t);
 * double param_3 = obj.getAverageTime(startStation,endStation);
 */
 ```
