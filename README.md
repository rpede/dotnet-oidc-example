# OpenID Connect example

Minimal working OpenID Connect client example based on
<https://learn.microsoft.com/en-us/aspnet/core/security/authentication/configure-oidc-web-authentication?view=aspnetcore-10.0>

## Setup

1. Start keycloak
    - `docker run -p 127.0.0.1:8080:8080 -e KC_BOOTSTRAP_ADMIN_USERNAME=admin -e KC_BOOTSTRAP_ADMIN_PASSWORD=admin quay.io/keycloak/keycloak:26.5.6 start-dev`
    - Replace `KC_BOOTSTRAP_ADMIN_PASSWORD` with a proper password
2. Open <http://localhost:8080/admin/>
3. Create a client with Client ID `oidc-example`
4. Under "Capability Config" enable "Client authentication"
5. Navigate to the new client. Under "Credentials" tab, copy "Client Secret"
6. Configure client secret:
    - `dotnet user-secrets init`
    - `dotnet user-secrets set "OpenIDConnectSettings:ClientSecret" "<client_secret>"`
    - Replace `<client_secret>` with the actual Client Secret
7. Test it
    - `dotnet run`
    - Open <http://localhost:5072/>
    - Click "Login" link then "OpenIdConnect" button
