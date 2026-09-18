# Current-user service boundary

Selected excerpt from the private implementation. Controllers receive the authenticated principal and delegate current-user resolution to one service boundary.

```csharp
public interface ICurrentUserResolver
{
    Task<CurrentUserResult?> ResolveAsync(ClaimsPrincipal principal);
}
```

The full result type and identity implementation are intentionally omitted. Browser-supplied owner IDs are not part of this boundary.
