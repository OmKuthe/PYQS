# Design Authentication Manager (Medium)

## Problem Statement:  
Design a system that manages authentication tokens for users. Each token has a time-to-live (TTL) and can be **generated**, **renewed**, and **counted** if unexpired.

## [LeetCode Problem](https://leetcode.com/problems/design-authentication-manager/)

---

### Approach:  

**Key Idea:**  
- Use a **HashMap** to store each token with its **expiry time**.  
- When a token is generated, record its expiry as `currentTime + timeToLive`.  
- On renewal, update the expiry if the token is still valid.  
- For counting, iterate through the map and check how many expiry times are still in the future.  

---

### Java Solution  

```java
import java.util.*;

class AuthenticationManager {
    private Map<String, Integer> TokenExpiry = new HashMap<>();
    private int life;

    public AuthenticationManager(int timeToLive) {
        life = timeToLive;
    }

    public void generate(String tokenId, int currentTime) {
        TokenExpiry.put(tokenId, life + currentTime);
    }

    public void renew(String tokenId, int currentTime) {
        if (TokenExpiry.getOrDefault(tokenId, -1) > currentTime) {
            TokenExpiry.put(tokenId, life + currentTime);
        }
    }

    public int countUnexpiredTokens(int currentTime) {
        int count = 0;
        for (int expiryTime : TokenExpiry.values()) {
            if (expiryTime > currentTime) {
                count++;
            }
        }
        return count;
    }
}

/**
 * Your AuthenticationManager object will be instantiated and called as such:
 * AuthenticationManager obj = new AuthenticationManager(timeToLive);
 * obj.generate(tokenId,currentTime);
 * obj.renew(tokenId,currentTime);
 * int param_3 = obj.countUnexpiredTokens(currentTime);
 */
