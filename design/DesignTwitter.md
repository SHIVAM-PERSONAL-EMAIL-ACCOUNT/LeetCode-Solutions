### Solution

```java
class Twitter {

    static class Tweet {
        int tweetId;
        int timeStamp;
        
        public Tweet(int tweetId, int timeStamp) {
            this.tweetId = tweetId;
            this.timeStamp = timeStamp;
        }
    }
    
    static class User {
        int userId;
        Set<Tweet> tweets;
        Set<Integer> followees;
        
        public User(int userId) {
            this.userId = userId;
            tweets = new HashSet<>();
            followees = new HashSet<>();
            followees.add(userId);
        }
    }
    
    Map<Integer,User> map; 
    int time;
    
    public Twitter() {
        map = new HashMap<>();
        time = 0;
    }
    
    public void recordUsers(int userId) {
       if (!map.containsKey(userId)) map.put(userId, new User(userId)); 
    }
    
    public void postTweet(int userId, int tweetId) {
        recordUsers(userId);
        User user = map.get(userId);
        user.tweets.add(new Tweet(tweetId,++time));
    }
    
    public List<Integer> getNewsFeed(int userId) {
        List<Integer> newsFeed = new LinkedList<>();
        User user = map.get(userId);
        if (user == null) return newsFeed;
        PriorityQueue<Tweet> pq = new PriorityQueue<>((t1,t2) -> t1.timeStamp - t2.timeStamp);
        for (Integer followeeId : user.followees) {
            User followee = map.get(followeeId);
            for (Tweet tweet : followee.tweets) {
                pq.offer(tweet);
                if (pq.size() > 10) pq.poll();
            }
        }
        while(!pq.isEmpty())
            newsFeed.add(0, pq.poll().tweetId);
        return newsFeed;
    }
    
    public void follow(int followerId, int followeeId) {
        recordUsers(followerId);
        recordUsers(followeeId);
        map.get(followerId).followees.add(followeeId);
    }
    
    public void unfollow(int followerId, int followeeId) {
        recordUsers(followerId);
        recordUsers(followeeId);
        map.get(followerId).followees.remove(followeeId);
    }
}

/**
 * Your Twitter object will be instantiated and called as such:
 * Twitter obj = new Twitter();
 * obj.postTweet(userId,tweetId);
 * List<Integer> param_2 = obj.getNewsFeed(userId);
 * obj.follow(followerId,followeeId);
 * obj.unfollow(followerId,followeeId);
 */
 ```
