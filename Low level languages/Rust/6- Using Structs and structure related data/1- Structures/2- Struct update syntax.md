### Creating Instances with Struct Update Syntax

```
fn main() {
    // --snip--

    let user2 = User {
        active: user1.active,
        username: user1.username,
        email: String::from("another@example.com"),
        sign_in_count: user1.sign_in_count,
    };
}

#or 

fn main() {
    // --snip--

    let user2 = User {
        email: String::from("another@example.com"),
        ..user1
    };
}
```

the `..`  specifies that the remaining fields not explicitly set should have the same value as the fields in the given instance.

It's not a shallow "copy all fields" — it **moves or copies each field individually**, following the same ownership rules as normal assignments.

|Field|Type|What happens|
|---|---|---|
|`username`|`String`|**Moved** into `user2`|
|`email`|`String`|**Not used** from `user1` (you provided a new one)|
|`active`|`bool`|**Copied** (`Copy` trait)|
|`sign_in_count`|`u64`|**Copied** (`Copy` trait)|

```
let user2 = User {
    email: String::from("new@example.com"),
    ..user1
};

// ❌ user1 — compiler error, partially moved
// ❌ user1.username — moved into user2
// ✅ user1.email — you provided a NEW string for user2's email,
//                  so user1.email was never touched
// ✅ user1.active — bool is Copy, still valid
// ✅ user1.sign_in_count — u64 is Copy, still valid
```

In this example, we can no longer use `user1` after creating `user2` because the `String` in the `username` field of `user1` was moved into `user2`.