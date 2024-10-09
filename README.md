# @intechnity/react-native-kanban-board

A kanban board for React Native.

<img src="./demo.gif" height="500">

## Installation

```sh
npm install @longwnx/react-native-kanban-board
```

react-native-gesture-handler must be also installed: https://www.npmjs.com/package/react-native-gesture-handler

## Usage

Import the necessary components and types:

```tsx
import { KanbanBoard, ColumnModel, CardModel } from '@intechnity/react-native-kanban-board';
```

Define the columns and cards:



```tsx
const data = [
  {
    "imgLinks": [],
    "iconName": [],
    "code": "CV0327",
    "name": "Test 4",
    "status": 2,
    "startDate": "2024-10-03T00:00:00",
    "endDate": "2024-10-31T00:00:00",
    "creationTime": "2024-10-03T09:09:15.061836",
    "id": 333
  },
  {
    "imgLinks": [],
    "iconName": [],
    "code": "CV0327",
    "name": "Test 3",
    "status": 2,
    "startDate": "2024-10-03T00:00:00",
    "endDate": "2024-10-31T00:00:00",
    "creationTime": "2024-10-03T09:09:15.061836",
    "id": 331
  },
  {
    "imgLinks": [
    ],
    "iconName": [],
    "code": "CV0327",
    "name": "Test 2",
    "status": 2,
    "startDate": "2024-10-03T00:00:00",
    "endDate": "2024-10-31T00:00:00",
    "creationTime": "2024-10-03T09:09:15.061836",
    "id": 329
  },
  {
    "imgLinks": [
    ],
    "iconName": [],
    "code": "CV0327",
    "name": "Test 1",
    "status": 2,
    "startDate": "2024-10-03T00:00:00",
    "endDate": "2024-10-31T00:00:00",
    "creationTime": "2024-10-03T09:09:15.061836",
    "id": 327
  },
];
```

```tsx
const columns = [
  new ColumnModel("statusTodo", "Todo", 1),
  new ColumnModel("inProgress", "In Progress", 2),
  new ColumnModel("ready", "Ready", 3),
];

const convertStatus = (status: number) => {
  switch (status) {
    case 0:
      return 'statusTodo';
    case 1:
      return 'inProgress';
    case 2:
      return 'ready';
    default:
      return 'statusTodo';
  }
};

const cards = works.list.map((item: WorkAssign) => {
  return new CardModel(
    item.id,
    convertStatus(item.status),
    item?.code,
    item?.priorityType,
    item?.name,
    '',
    '',
    [],
    item,
    1
  );
}, []);

```

Create event handlers:

```ts
const onCardDragEnd = (srcColumn: ColumnModel, destColumn: ColumnModel, item: CardModel, targetIdx: number) => {
  // Handle card drag and drop
};

const onCardPress = (item: CardModel) => {
  // Handle card press
};

```

Render the Kanban Board component:

```tsx
<KanbanBoard
  columns={columns}
  cards={cards}
  onDragEnd={onCardDragEnd}
  onCardPress={onCardPress}
/>

```
Or

```tsx
<KanbanBoard
  columns={columns}
  cards={cards}
  onDragEnd={onCardDragEnd}
  style={{flex: 1}}
  columnHeaderTitleStyle={{fontWeight: '600', fontSize: 16}}
  renderCardContent={renderCardContent}
/>

```

## API

### KanbanBoardProps

- `columns: ColumnModel[]`\
  An array of `ColumnModel` instances representing the columns on the Kanban board.

- `cards: CardModel[]`\
  An array of `CardModel` instances representing the cards within the columns.

- `onCardPress?: (model: CardModel) => void`\
  Callback function invoked when a card is pressed.

- `onDragEnd: (srcColumn: ColumnModel, destColumn: ColumnModel, item: CardModel, targetIdx: number) => void`\
  Callback function invoked when a card is dragged and dropped onto another column. It receives the following parameters:
  - `srcColumn: ColumnModel` - The source column from which the card was dragged.
  - `destColumn: ColumnModel` - The destination column where the card was dropped.
  - `item: CardModel` - The card that was dragged and dropped.
  - `targetIdx: number` - The index at which the card was dropped within the destination column.

- `renderCardContent?(model: CardModel): JSX.Element | null`\
  Optional custom renderer for the card content.

- `renderEmptyColumn?: (item: ColumnModel) => JSX.Element`\
  Optional custom renderer for an empty column.

- `cardContainerStyle?: StyleProp<ViewStyle>`\
  Custom style for the card container.

- `cardTitleTextStyle?: StyleProp<TextStyle>`\
  Custom style for the card title text.

- `cardSubtitleTextStyle?: StyleProp<TextStyle>`\
  Custom style for the card subtitle text.

- `cardContentTextStyle?: StyleProp<TextStyle>`\
  Custom style for the card content text.

- `columnHeaderContainerStyle?: StyleProp<ViewStyle>`\
  Custom style for the column header container.

- `columnHeaderTitleStyle?: StyleProp<TextStyle>`\
  Custom style for the column header title.


**Note:** `StyleProp<ViewStyle>` and `StyleProp<TextStyle>` are types from the `react-native` package and are used to define custom styles for components.


## Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## License

MIT

------

## TODO
- Render custom column
- Input margin/paddings
- Overhaul of KanbanContext Provider
- Style cards count indicator
- Tests
- CI linting
