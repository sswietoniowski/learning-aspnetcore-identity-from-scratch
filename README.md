# Learning ASP.NET Core - Identity From Scratch
 
Small demo of how ASP.NET Core Identity can be used.
 
# Useful commands

dotnet new globaljson --sdk-version 5.0.400 --output IdentityTodo
dotnet new webapp --auth Individual --use-local-db true --output IdentityTodo --framework net5.0
dotnet new sln -o IdentityTodo
dotnet sln IdentityTodo add IdentityTodo


dotnet new globaljson --sdk-version 5.0.400 --output IdentityApp
dotnet new web --no-https --output IdentityApp --framework net5.0
dotnet new sln -o IdentityApp
dotnet sln IdentityApp add IdentityApp


dotnet tool uninstall --global Microsoft.Web.LibraryManager.Cli
dotnet tool install --global Microsoft.Web.LibraryManager.Cli --version 2.1.113
libman init -p cdnjs
libman install twitter-bootstrap@4.5.0 -d wwwroot/lib/twitter-bootstrap

dotnet add package Microsoft.EntityFrameworkCore.Design --version 5.0.0
dotnet add package Microsoft.EntityFrameworkCore.SqlServer --version 5.0.0

libman install qrcodejs@1.0.0 -d wwwroot/lib/qrcode

# Identity UI package

Account/Register
Account/RegisterConfirmation
Account/ResendEmailConfirmation
Account/ConfirmEmail
Account/Login
Account/Logout
Account/ExternalLogin
Account/SetPassword
Account/Lockout
Account/Manage/TwoFactorAuthentication
Account/Manage/EnableAuthenticator
Account/Manage/ResetAuthenticator
Account/Manage/GenerateRecoveryCodes
Account/Manage/ShowRecoveryCodes
Account/Manage/Disable2fa
Account/LoginWith2fa
Account/LoginWithRecoveryCode
Account/ForgotPassword
Account/ForgotPasswordConfirmation
Account/ResetPassword
Account/ResetPasswordConfirmation
Account/Manage/Index
Account/Manage/ChangePassword
Account/Manage/Email
Account/ConfirmEmailChange
Account/Manage/PersonalData
Account/Manage/DownloadPersonalData
Account/Manage/DeletePersonalData
Account/AccessDenied

# External authenticator

## Facebook

https://developers.facebook.com/apps

dotnet user-secrets init
dotnet user-secrets set "Facebook:AppId" "<app-id>"
dotnet user-secrets set "Facebook:AppSecret" "<app-secret>"

## Google

dotnet user-secrets init
dotnet user-secrets set "Google:ClientId" "<client-id>"
dotnet user-secrets set "Google:ClientSecret" "<client-secret>"

## Tweeter

dotnet user-secrets init
dotnet user-secrets set "Twitter:ApiKey" "<client-id>"
dotnet user-secrets set "Twitter:ApiSecret" "<client-secret>"

## Adapting Identity UI

dotnet tool uninstall --global dotnet-aspnet-codegenerator
dotnet tool install --global dotnet-aspnet-codegenerator --version 5.0.0

dotnet aspnet-codegenerator identity --listFiles

libman install font-awesome@5.15.1 -d wwwroot/lib/font-awesome

dotnet aspnet-codegenerator identity --dbContext Microsoft.AspNetCore.Identity.EntityFrameworkCore.IdentityDbContext --files Account.Login
dotnet aspnet-codegenerator identity --dbContext Microsoft.AspNetCore.Identity.EntityFrameworkCore.IdentityDbContext --files Account.Register

dotnet aspnet-codegenerator identity --dbContext Microsoft.AspNetCore.Identity.EntityFrameworkCore.IdentityDbContext --files "Account.Manage._Layout;Account.Manage._ManageNav"

# Testing the Authentication API

Run from wwwroot:

npx http-server -p 5100 -c-1
