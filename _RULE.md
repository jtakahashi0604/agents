# RULE

----------------------------------------------------------------

## 1. Style

### Command

#### Package manager
- Do use `pnpm` and `pnpx`.

#### Prisma
- Do use `pnpm prisma` and your commands.
- Do not use migration name.

### File

#### Name

- Camel case(`camelCase`, `CamelCase`)

### Code

- Following Biome
- Avoid writing comments whenever possible

#### Name

- Camel case(`camelCase`, `CamelCase`)

#### Function

##### Parameters

Do use named parameters.

```ts
function foo({ bar }: { bar: string }) {
  return bar;
}
```

#### Condition

Do use `== null` if you want to check if a value is null or undefined.

✅
```tsx
if (value == null) {
  return null;
}
```

❌
```tsx
if (!value) {
  return value;
}
```

#### Elements in tsx

##### Tailwind CSS

###### Use even numbers

✅
```tsx
<div className="p-2">
  hi
</div>
```

❌
```tsx
<div className="p-3">
  hi
</div>
```

###### Use Spacing

✅
```tsx
- space-*
- p*
- gap-*
```

❌
```tsx
- m*
```

###### Spacing between elements

Do not use space between A element and B element in tsx.

✅
```tsx
<div>
  hi 1
</div>
<div>
  hi 2
</div>
<div>
  hi 3
</div>
```

❌
```tsx
<div>
  hi 1
</div>

<div>
  hi 2
</div>

<div>
  hi 3
</div>
```

### Code - Test

#### Organization

```
[define]
[:BLANK_LINE:]
[action]
[:BLANK_LINE:]
[render]
[:BLANK_LINE:]
[expect]
```

#### Value

##### Single value in a test case

```
id:    "example-id"
value: "Test Example"
```

##### Single value in a test case for update

```
id:    "example-id"
value: "Updated Test Example"
```

##### Multi value

```
id:    "example-1-id"
value: "Test Example 1"

id:    "example-2-id"
value: "Test Example 2"
```

##### Multi tenant and value

```
id:    "tenant-1-id"
value: "Tenant 1"

id:    "tenant-2-id"
value: "Tenant 2"

id:    "tenant-1-example1-id"
value: "Tenant 1 - Test Example 1"

id:    "tenant-1-example2-id"
value: "Tenant 1 - Test Example 2"

id:    "tenant-2-example1-id"
value: "Tenant 2 - Test Example 1"

id:    "tenant-2-example2-id"
value: "Tenant 2 - Test Example 2"
```

#### Description

##### Service

###### findMany
- returns examples for the specified team
- returns empty array when no examples exist
- returns examples sorted by createdAt descending

###### findById
- returns the example when it exists
- throws error when example does not exist
- throws error when example belongs to different team

###### create
- creates a new example
- creates example with correct team association

###### update
- updates an existing example
- throws error when example belongs to different team

###### remove
- removes an existing example
- throws error when example belongs to different team

##### Component

###### list
- renders empty state when no examples provided
- renders list of examples
- renders links to example detail pages
- calls create action when Create button is clicked

###### form
- renders form with example data
- updates input value when user types
- calls update action when Submit button is clicked
- calls remove action when Remove button is clicked
- shows validation error

##### Policy
- allows access when example belongs to the team
- throws error when example does not exist
- throws error when example belongs to different team

----------------------------------------------------------------

## 2. Design

### KISS

- Keep it simple, stupid.

### DRY

- Do not repeat yourself.

### SOLID

- SRP
  - One func = One role.
- OCP
- LSP
- ISP
  - Interface is small.
- DIP
  - Upper-level modules
    should not depend on
    lower-level modules.

----------------------------------------------------------------

## 3. Maintainability

### Name

- ✅ Do use meaningful names and descriptions.
  - If it is a function, do use verb.
  - If it is a variable, do use noun.
  - If it has side effect, do show it.
- ❌ Do not use vague names.
  - `data`.
  - `info`.
  - `temp`.

### Comment

- ✅ Do use meaningful comments.
  - Directly describe the code.
  - It needs to be improved.
  - Constant value meaning.

### Flow

- ✅ Do use early return statements.
- ⚠️ Do use map functions instead of for loops.
- ❌ Do not use nested conditions.
- ❌ Do not use multiple flow control variables.
  - ex) `is-` and `-ed` and ...
- ❌ Do not use goto statements.

----------------------------------------------------------------

## 4. Testability

- ✅ Do use meaningful names and descriptions.
- ✅ Do use minimal variables but cover all cases.

----------------------------------------------------------------

## 5. Reliability

- ✅ Do handle errors gracefully.
- ✅ Do handle retry and timeout.
  - Operating Database
  - Operating File System
  - Operating Network
- ⚠️ Do record necessary logs.

----------------------------------------------------------------

## 6. Correctness

- ❌ Do not allow duplicate requests.
- ✅ Do keep consistency for any logic.

- Follow _SPEC.md

----------------------------------------------------------------

## 7. Performance

- ❌ Do not over calc cost O(n^2).
- ❌ Do not use N+1 queries.

----------------------------------------------------------------

## 8. Security

- ✅ Do [MUST] check auth.
- ✅ Do [MUST] check permission for multi-tenant scope.
- ✅ Do [MUST] check for embedded secrets in the code.
- ✅ Do [MUST] check for vulnerability patterns.
  - Scope
    - CORS
    - Cookie
  - * Injection
  - Hijacking
    - Session
    - Token
    - Click
  - XSS
  - CSRF
  - SSRF
  - RCE
  - IDOR
