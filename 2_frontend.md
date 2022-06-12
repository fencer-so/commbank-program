# Frontend
## Update the Goal Interface

```ts
// types.ts

export interface Goal {
    iconName: string;
}
```

## Update `GoalCard`
```ts
// GoalCard.tsx

export default function GoalCard(props: Props) {
  const dispatch = useAppDispatch();

  const goal = useAppSelector(selectGoalsMap)[props.id];

  const onClick = (e: React.MouseEvent) => {
    e.stopPropagation()
    dispatch(setContent(goal))
    dispatch(setType("Goal"))
    dispatch(setIsOpen(true))
  }

  const asLocaleDateString = (date: Date) => new Date(date).toLocaleDateString();

  return (
    <Container key={goal.id} className='card' onClick={onClick}>
      <TargetAmount>${goal.targetAmount}</TargetAmount>
      <TargetDate>{asLocaleDateString(goal.targetDate)}</TargetDate>
      <Icon>{goal.iconName}</Icon>
    </Container>
  )
}
```