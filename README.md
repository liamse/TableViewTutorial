# How to use react-native-tableview

This is an iOS only react-native package which implemente iOS UITableView. For this toturial we use following packages:

- react-native@0.55.4
- react-native-tableview@2.1.0

## Step 0

To start your project you need to initialize a react-native project, so here's the installation commands for what we need to start:

As react-native document wrote, we have two method to init a react-native project. I build my project with native code. If you would like to know more about Expo method you can find good information about it on [react-native getting start](https://facebook.github.io/react-native/docs/getting-started.html) document.

```bash
# init a project with name TableViewTutorial
react-native init TableViewTutorial

# open the folder
cd TableViewTutorial
# open ios folder, in this tutorial the Android is not used
cd ios

# open xcodeproj. This command open xcode application and this project
open TableViewTurorial.xcodeproj
```

Until here if you run your project, it install on simulator or your iphone and you can see the welcome message of react-native.

Now install `react-native-tableview` as its [github](https://github.com/aksonov/react-native-tableview) documentation suggest.

```bash
yarn add react-native-tableview
# or
npm install react-native-tableview --save

# and link it
react-native link react-native-tableview
```

Link a react-native copy related library of package and set proper settings on xcode to the package can work properly. After link the package you can find it under Library folder at xcode as `RNTableView.xcode`.

## Step 1

Create `Example1.js` file in `src` folder. I copy the content of it exactly from react-native-tableview [Example1](https://github.com/aksonov/react-native-tableview/blob/master/example/src/screens/Example1.js).

```js
import React, { Component } from 'react';
import TableView from 'react-native-tableview';
const { Section, Item } = TableView

const Example1 = () => (
    <TableView
        style={{ flex: 1 }}
        allowsToggle
        allowsMultipleSelection
        tableViewStyle={TableView.Consts.Style.Grouped}
        tableViewCellStyle={TableView.Consts.CellStyle.Subtitle}
        onPress={event => console.log(event)}
    >
        <Section label="Section 1" arrow>
            <Item value="1" detail="Detail1">Item 1</Item>
            <Item value="2">Item 2</Item>
            <Item>Item 3</Item>
        </Section>

        <Section label="Section 2" arrow={false}>
            <Item>Item 1</Item>
            <Item>Item 2</Item>
            <Item>Item 3</Item>
        </Section>

        <Section label="Section 3" arrow={false}>
            <Item>Item 1</Item>
            <Item>Item 2</Item>
            <Item>Item 3</Item>
        </Section>
    </TableView>
)
export default Example1
```

Change `App.js` file as following code and refress app to **SEE NOTHING**, only a light blue background.

```js
import React, { Component } from 'react';
import Example1 from './src/Example1'

type Props = {};

export default class App extends Component<Props> {
  render() {
    return (
      <View style={styles.container}>
        <Example1 />
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center', // This sets width of TableView to zero
    backgroundColor: '#F5FCFF',
  },
});
```

The problem is `alignItems: 'center'` in `container` folder. Omit it or change it to `stretch` solves the problem. I omit it.

## step 2

Every `TableView` must have at least one `Section` component.`TableView` by itself doesn't render anything, you have to add a Section.

```js
<TableView>
  <Section>
  </Section>
</TableView>
```

Until here we render a `TableView`.
