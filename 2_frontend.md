# Frontend
## Update The Goal Model

```ts
// types.ts

export interface Goal {
    iconName: string;
}
```

## Update The Card Component
```ts
// GoalCard.tsx

export default function GoalCard(props: Props) {
  const dispatch = useAppDispatch()

  const goal = useAppSelector(selectGoalsMap)[props.id]

  const onClick = (event: React.MouseEvent) => {
    event.stopPropagation()
    dispatch(setContentRedux(goal))
    dispatch(setTypeRedux('Goal'))
    dispatch(setIsOpenRedux(true))
  }

  const asLocaleDateString = (date: Date) => new Date(date).toLocaleDateString()

  return (
    <Container key={goal.id} onClick={onClick}>
      <TargetAmount>${goal.targetAmount}</TargetAmount>
      <TargetDate>{asLocaleDateString(goal.targetDate)}</TargetDate>
      <Icon>{goal.iconName}</Icon>
    </Container>
  )
}
```

## Install `EmojiMart` @[v3.0.1](https://github.com/missive/emoji-mart/tree/v3.0.1)

> ⚠️ **v5.1.0 HAS BREAKING CHANGE:** USE v3.0.1

```shell
npm install --save emoji-mart@3.0.1
```

## Update The Goal Manager

### `Case 1`: Goal Has No Icon

#### Add An `AddIcon` Button That Is Only Visible When There Is No Icon

```ts
// GoalManager.tsx

export function GoalManager(props: Props) {

    const [icon, setIcon] = useState<string | null>(null)

    const hasIcon = () => icon != null
    
    const addIconOnClick = (event: React.MouseEvent) => {
      event.stopPropagation()
      setEmojiPickerIsOpen(true)
    }

    return (
      <AddIconButtonContainer hasIcon={hasIcon()}>
        <TransparentButton onClick={addIconOnClick}>
          <FontAwesomeIcon icon={faSmile} size="2x" />
          <AddIconButtonText>Add icon</AddIconButtonText>
        </TransparentButton>
      </AddIconButtonContainer>
    )
}

```

#### `Case 2`: Goal Has Icon
#### Display The Icon When It Is Available

```ts
// GoalModal.tsx

```