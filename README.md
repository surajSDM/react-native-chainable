# react-native-chainable

🔗 Chain through your React Native forms with ease

## Installation

```sh
npm install react-native-chainable --save

# or

yarn add react-native-chainable
```

## Usage

```jsx
import { Chainable } from 'react-native-chainable';

export default class SignUpScreen extends React.Component {
  // ...

  render() {
    return (
      <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
        <Chainable>
          {chain => (
            <React.Fragment>
              <Chainable.Input
                style={{ width: 150, borderWidth: 1, borderColor: 'dimgrey' }}
                value={this.state.email}
                onChangeText={text => this.setState({ email: text })}
                onSubmitEditing={() => chain('password')}
              />
              <Chainable.Input
                name="password"
                style={{ width: 150, borderWidth: 1, borderColor: 'dimgrey' }}
                secureTextEntry
                value={this.state.password}
                onChangeText={text => this.setState({ password: text })}
                onSubmitEditing={() => chain('confirm')}
              />
              <Chainable.Input
                name="confirm"
                style={{ width: 150, borderWidth: 1, borderColor: 'dimgrey' }}
                secureTextEntry
                value={this.state.confirm}
                onChangeText={text => this.setState({ confirm: text })}
                isLast
              />
            </React.Fragment>
          )}
        </Chainable>
      </View>
    );
  }
}
```

## API

`<Chainable />`

### Render prop (function as a child)

The function you pass as a child will be called with a function that allows you to chain to (i.e. set focus on) the next input by name

| Type                   | Description                                 |
| ---------------------- | ------------------------------------------- |
| (name: string) => void | Function to chain to the next input by name |

`<Chainable.Input />`

### Props

| Name   | Type                                    | Description                                                 |
| ------ | --------------------------------------- | ----------------------------------------------------------- |
| name   | string (**required**)                   | A name for the input                                        |
| isLast | boolean (optional, defaults to `false`) | When `true`, the input should be considered as the last one |
