# Modify The Goal Manager So Users Can Add And Change Icons

- [ ] Add an `AddIcon` button that:
  - [ ] Is only visible when there is no icon
  - [ ] Opens the emoji picker component

```ts
// GoalManager.tsx

export function GoalManager(props: Props) {
  const [icon, setIcon] = useState<string | null>(null)

  useEffect(() => {
    setIcon(props.goal.icon)
  }, [props.goal.id, props.goal.icon])

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

- [ ] Add an `Icon` component that:
  - [ ] Is only visible when there is an icon
  - [ ] Uses `TransparentButton` component
  - [ ] Opens the emoji picker component

```ts
// GoalManager.tsx

type GoalIconContainerProps = { shouldShow: boolean }

const GoalIconContainer = styled.div<GoalIconContainerProps>`
  display: ${(props) => (props.shouldShow ? 'flex' : 'none')};
`

export function GoalManager(props: Props) {
  const hasIcon = () => icon != null

  const goal = useAppSelector(selectGoalsMap)[props.goal.id]

  return (
    <GoalIconContainer shouldShow={hasIcon()}>
      <GoalIcon icon={goal.icon} onClick={addIconOnClick} />
    </GoalIconContainer>
  )
}
```
