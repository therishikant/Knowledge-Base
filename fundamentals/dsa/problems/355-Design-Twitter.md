# 355. Design Twitter

#### Intution:
- 1. user **maxHeap** to track to lastest tweets: (Not able to code)
  - ##### Failed:
    - Insertion order will not be maintianed 
    - tweetId is random -> Overcome by adding post time
    - remove tweets older than 10 (assuming tweetId is acting as time) -> But it is wrong 
- 2. use normal list with custom post time (Able to code)
  - treat tweetId as a hash-value
  - need to maintain custom post time
  - getNewsFeed() -> return last 10 tweets
  
#### Impl

#### My Approch
```python
class Twitter:

    def __init__(self):
        self.myTweetsMap = defaultdict(list) # (UserId, [tweets])
        self.followerMap = defaultdict(list) # (userId, [followers])
        self.allTweetMap = defaultdict(list) # (userId, [tweets])
        self.time = 0

    def postTweet(self, userId: int, tweetId: int) -> None:
        self.time += 1
        # Add tweet into tweetsMap
        self.myTweetsMap[userId].append((self.time, tweetId))
        self.allTweetMap[userId].append((self.time, tweetId))
        # Add tweet into allTweetMap of followers
        for follower in self.followerMap[userId]:
            self.allTweetMap[follower].append((self.time, tweetId))

    def getNewsFeed(self, userId: int) -> List[int]:
        # return maxHeap
        res = []
        self.allTweetMap[userId].sort(reverse=True)
        for i in range(10):
            if len(self.allTweetMap[userId]) > i:
                res.append(self.allTweetMap[userId][i][1])
        return res

    def follow(self, followerId: int, followeeId: int) -> None:
        # add follower into followerMap
        if followerId in self.followerMap[followeeId]:
            return
        self.followerMap[followeeId].append(followerId)
        for time, tweetId in self.myTweetsMap[followeeId]:
            self.allTweetMap[followerId].append((time, tweetId))

    def unfollow(self, followerId: int, followeeId: int) -> None:
        # remove follower from followerMap
        if followerId not in self.followerMap[followeeId]:
            return
        self.followerMap[followeeId].remove(followerId)
        
        finalTweets = list(set(self.allTweetMap[followerId]) - set(self.allTweetMap[followeeId]))
        for time, tweetId in self.myTweetsMap[followerId]:
            finalTweets.append((time, tweetId))
        finalTweets = list(set(finalTweets))

        self.allTweetMap[followerId] = finalTweets
```

#### Optimal Approch
- Use two map
- only calculate when needed

```python
from collections import defaultdict
import heapq

class Twitter:

    def __init__(self):
        self.tweetMap = defaultdict(list)
        self.followMap = defaultdict(set)
        self.time = 0

    def postTweet(self, userId: int, tweetId: int) -> None:
        self.time += 1
        self.tweetMap[userId].append((self.time, tweetId))

    def getNewsFeed(self, userId: int):
        res = []
        heap = []

        # user follows himself
        self.followMap[userId].add(userId)

        for followee in self.followMap[userId]:
            if followee in self.tweetMap:
                index = len(self.tweetMap[followee]) - 1
                time, tweetId = self.tweetMap[followee][index]
                heapq.heappush(heap, (-time, tweetId, followee, index - 1))

        while heap and len(res) < 10:
            time, tweetId, user, index = heapq.heappop(heap)
            res.append(tweetId)

            if index >= 0:
                time, tweetId = self.tweetMap[user][index]
                heapq.heappush(heap, (-time, tweetId, user, index - 1))

        return res

    def follow(self, followerId: int, followeeId: int) -> None:
        self.followMap[followerId].add(followeeId)

    def unfollow(self, followerId: int, followeeId: int) -> None:
        if followeeId != followerId:
            self.followMap[followerId].discard(followeeId)
```