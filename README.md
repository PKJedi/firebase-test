
# Firebase demo

Simple firebase demo, lives on firebase hosting. Cooperatively spam characters.

## Live

https://shining-torch-5768.firebaseapp.com

## Firebase rules
```
{
  "rules": {
    "users": {
      ".read": "true",
      "$uid": {
        // grants write access to the owner of this user account whose uid must exactly match the key ($uid)
        ".write": "auth !== null && auth.uid === $uid",
        
        // grants read access to any user who is logged in anonymously
        ".read": "auth !== null && auth.provider === 'anonymous'",
        
        ".validate": "newData.child('character').isString() && newData.child('character').val().length === 1 && newData.child('timestamp').val() === now"
      }
    }
  }
}
```

