Front Code is same as the Basic Authentication Example except for a small change.

This is an extract from `class LoginComponent extends Component {` in the frontend project for [Basic Authentication](https://github.com/in28minutes/spring-boot-react-fullstack-examples/tree/master/spring-boot-react-basic-auth-login-logout/frontend-spring-boot-react-basic-auth-login-logout)

```
        AuthenticationService
            .executeBasicAuthenticationService(this.state.username, this.state.password)
            .then(() => {
                AuthenticationService.registerSuccessfulLogin(this.state.username, this.state.password)
                this.props.history.push(`/courses`)
            }).catch(() => {
                this.setState({ showSuccessMessage: false })
                this.setState({ hasLoginFailed: true })
            })

        // AuthenticationService
        //     .executeJwtAuthenticationService(this.state.username, this.state.password)
        //     .then((response) => {
        //         AuthenticationService.registerSuccessfulLoginForJwt(this.state.username, response.data.token)
        //         this.props.history.push(`/courses`)
        //     }).catch(() => {
        //         this.setState({ showSuccessMessage: false })
        //         this.setState({ hasLoginFailed: true })
        //     })
```

Comment out the Basic Authentication and Un Comment the JWT Authentication Call.

This is how the code should look like!

```
        // AuthenticationService
        //     .executeBasicAuthenticationService(this.state.username, this.state.password)
        //     .then(() => {
        //         AuthenticationService.registerSuccessfulLogin(this.state.username, this.state.password)
        //         this.props.history.push(`/courses`)
        //     }).catch(() => {
        //         this.setState({ showSuccessMessage: false })
        //         this.setState({ hasLoginFailed: true })
        //     })

        AuthenticationService
            .executeJwtAuthenticationService(this.state.username, this.state.password)
            .then((response) => {
                AuthenticationService.registerSuccessfulLoginForJwt(this.state.username, response.data.token)
                this.props.history.push(`/courses`)
            }).catch(() => {
                this.setState({ showSuccessMessage: false })
                this.setState({ hasLoginFailed: true })
            })
```