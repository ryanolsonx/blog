# // Why Comments
Let's explore why you should add comments to your source code (or not).

## Good Code is Self-Documenting
It's widely accepted that good code should be self-documenting, but in many cases, this notion has become more of a cliché than a helpful guideline. Some engineers take this mantra to an extreme, avoiding comments at all costs and believing that doing so is a sign of good coding practices. While it's true that writing code that is self-documenting increases readability, comments can still play an important role in making your code more readable and maintainable.

## Let's Look at Bad Comments
Calling Others Out
...Just don't.

```
/* Class used to workaround Richard being
an idiot */

// This code sucks. Just use it. Call me
// an idiot later.

// This code is a bit slow because Alex
// added that stupid hook…
```

## Describing What You're Doing
Although it can be tempting to add comments to explain what your code is doing, doing so may actually duplicate information that is already evident in the code itself, potentially creating unnecessary complexity and reducing the clarity and maintainability of the code.

From TypeScripts Codebase:
```js
// Enable portable support
bootstrap.configurePortable();
// Enable ASAR support
bootstrap.enableASARSupport();
```

If you're writing a program that includes user preferences that someone can retrieve:

```js
export const getUserPreferences = id => {
  // Get the user
  const user = userService.getUser({
    id: 15
  });
	
  // Get users preferences and sort by created date
  const preferences =
    user.preferences.sort(sortBy(‘createdDate’));
	
  // Return the user preferences
  return preferences;
}
```

## Not Self-Documenting
When code lacks self-documentation, there may be a tendency to rely on comments to explain it. If this is the case, it's important to recognize the value of self-documenting code and work to restructure the code in a more understandable and intuitive way.

From React.js Codebase (since removed):

```js
if (!existsSync('./scripts/results.json')) {
  // This indicates the build failed
  // previously. In that case,
  // there's nothing for the Dangerfile
  // to do. Exit early to avoid leaving
  // a redundant (and potentially
  // confusing) PR comment.
  process.exit(0);
}
```

This can be rewritten as:

```js
if (hasBuildFailedPreviously()) {
  process.exit(0);
}
```

## Excuse for Writing Bad Code
Comments should not be used as a justification for writing poor quality code, such as hacks or workarounds. While it may be tempting to add comments to excuse a suboptimal code solution, this approach can ultimately make the code more difficult to maintain and may obscure the underlying problem. Instead, it's important to focus on improving the code itself, rather than relying on comments to mask deficiencies. If there is a NEED for the hack, then of course, provide a comment as to why the hack is there.

```js
// Writing this using splice because I couldn’t figure out slice.. :(
const userNames = users.splice(5).map(user => user.name);

// I know I should memoize this but I don’t have time to do that
const notes = notes.filter(isShown).map(note => note.value);
```

## "Why" Comments
When adding comments to your code, it's essential to include explanations of why you made certain design choices or implemented certain functions in a particular way. These "why" comments can provide crucial context to other developers who may need to work with your code in the future, helping to ensure that the code remains maintainable and understandable over time.

## Explaining Your Approach
In certain situations, you may find yourself implementing a solution in a way that may not seem intuitive or optimal at first glance. By including comments that explain the reasoning behind your approach, you can save time and frustration for future readers of your code who may be wondering why you took that particular path. This can help them better understand the problem you were trying to solve and potentially come up with more efficient solutions in the future.

```js
// A binary search turned out to be slower than the Boyer-Moore algorithm
// for the data sets of interest, thus we have used the more complex, but
// faster method even though this problem does not at first seem amenable to a
// string search technique.
const searchForFund = (searchQuery) => {
  // Implementation here
}
```

## Documenting External Factors
When writing code, it's important to consider external factors that may impact future modifications. By including comments that document these factors, you can make it easier for future developers to make changes to your code without introducing unintended consequences. For example, you might need to explain why a certain function should not be modified, or warn about potential conflicts with other parts of the system. These comments can be invaluable in preventing costly errors and reducing the time it takes to make changes to the codebase.

```js
def user_avatar_path(user_profile):
  # WARNING: If this method is changed, you may need to do
  # a migration similar to
  # zerver/migrations/0060_move_avatars_to_be_uid_based.py
  return user_avatar_path_from_ids(user_profile.id, user_profile.realm_id)
```

## Clarifying the Code
In the React.js codebase, there may be some parts that are difficult to understand at first glance. For instance, in this function, assigning the reactRootContainer to container._reactRootContainer might be confusing to some. However, by adding clarifying comments about the reason for this code, you can make the code more understandable to future developers who may need to work on it. In the example below, the comments explain how the container might be used for a portal and why it's important to ensure that non-React root containers have inline onclick defined, providing a link to further information on the issue.

```js
// This container might be used for a portal.
// If something inside a portal is clicked, that click should bubble
// through the React tree. However, on Mobile Safari the click would
// never bubble through the *DOM* tree unless an ancestor with onclick
// event exists. So we wouldn't see it and dispatch it.
// This is why we ensure that non React root containers have inline onclick
// defined.
// https://github.com/facebook/react/issues/11918
const reactRootContainer = container._reactRootContainer;
```

## Clarifying Business Requirements through Code Comments
Even with well-organized and self-documenting code, it's not always apparent what the business requirements are and why certain decisions were made. By including comments that provide context and clarification, you can help future developers understand the purpose behind the code and make better decisions when modifying it.

```js
// Since notifications may not always have an email, it's necessary to detect
// this scenario and attempt to send emails only to those with a defined email
// address. Although all notifications will eventually be required to have an
// email, the product team has specified that we do it this way for now.
const sendEmailNotifications = (notifications) => {
  const toSend = notifications.filter(hasEmail);
  return sendEmails(toSend);
}
```

## Why Comments
In conclusion, adding comments to your code that explain the reasoning behind why it's written the way it is can save future developers time, help them understand the code better, and prevent mistakes from being made. It can also make it easier to maintain and update the codebase, especially in cases where external factors or business requirements play a role. By taking the time to write clear and concise "why" comments, you can make your code more readable, maintainable, and ultimately more valuable.
