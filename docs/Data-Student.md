# <a name="module-data-student-28646"></a>Module Data.Student

## Data Types

<a name="type-data-student-student-55208"></a>**data** [Student](#type-data-student-student-55208)

> <a name="constr-data-student-student-97081"></a>[Student](#constr-data-student-student-97081)
>
> > | Field | Type  | Description |
> > | :---- | :---- | :---------- |
> > | name  | Text  |  |
> > | party | Party |  |
>
> **instance** Eq [Student](#type-data-student-student-55208)
>
> **instance** Ord [Student](#type-data-student-student-55208)
>
> **instance** Show [Student](#type-data-student-student-55208)
>
> **instance** HasField "grantedSwap" [Class](Class.html#type-class-class-70181) (Set [Student](#type-data-student-student-55208))
>
> **instance** HasField "name" [Student](#type-data-student-student-55208) Text
>
> **instance** HasField "party" [Student](#type-data-student-student-55208) Party
>
> **instance** HasField "student" AddStudent [Student](#type-data-student-student-55208)
>
> **instance** HasField "student" DropStudent [Student](#type-data-student-student-55208)
>
> **instance** HasField "student" [ClassSwap](ClassSwap.html#type-classswap-classswap-72105) [Student](#type-data-student-student-55208)
>
> **instance** HasField "student" [ClassTransfer](Cycle.html#type-cycle-classtransfer-9450) [Student](#type-data-student-student-55208)
>
> **instance** HasField "students" [Class](Class.html#type-class-class-70181) (Set [Student](#type-data-student-student-55208))
