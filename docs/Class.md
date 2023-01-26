# <a name="module-class-5316"></a>Module Class

## Templates

<a name="type-class-class-70181"></a>**template** [Class](#type-class-class-70181)

> A Class Template
>
> Class contracts represent classes that exist for the current semester.
> The registrar can create a class, swap students, finialize the registration, or archive it
> after the semester is over.
>
> | Field                                                            | Type                                                             | Description |
> | :--------------------------------------------------------------- | :--------------------------------------------------------------- | :---------- |
> | bio                                                              | [ClassBio](#type-class-classbio-22732)                           |  |
> | registrar                                                        | Party                                                            |  |
> | professor                                                        | Party                                                            |  |
> | students                                                         | Set [Student](Data-Student.html#type-data-student-student-55208) |  |
> | grantedSwap                                                      | Set [Student](Data-Student.html#type-data-student-student-55208) |  |
> | finalized                                                        | Bool                                                             |  |
>
> * **Choice AddStudent**
>
>   | Field                                                        | Type                                                         | Description |
>   | :----------------------------------------------------------- | :----------------------------------------------------------- | :---------- |
>   | student                                                      | [Student](Data-Student.html#type-data-student-student-55208) |  |
>   | fromTrade                                                    | Bool                                                         |  |
>
> * **Choice Archive**
>
>   (no fields)
>
> * **Choice CloseRegistration**
>
>   (no fields)
>
> * **Choice DropStudent**
>
>   | Field                                                        | Type                                                         | Description |
>   | :----------------------------------------------------------- | :----------------------------------------------------------- | :---------- |
>   | student                                                      | [Student](Data-Student.html#type-data-student-student-55208) |  |

## Data Types

<a name="type-class-classbio-22732"></a>**data** [ClassBio](#type-class-classbio-22732)

> A bio of a class that doesn't change
> across semesters
>
> <a name="constr-class-classbio-58973"></a>[ClassBio](#constr-class-classbio-58973)
>
> > | Field       | Type        | Description |
> > | :---------- | :---------- | :---------- |
> > | title       | Text        |  |
> > | description | Text        |  |
> > | code        | Text        |  |
> > | uid         | Int         |  |
>
> **instance** Eq [ClassBio](#type-class-classbio-22732)
>
> **instance** Ord [ClassBio](#type-class-classbio-22732)
>
> **instance** Show [ClassBio](#type-class-classbio-22732)
>
> **instance** HasField "bio" [Class](#type-class-class-70181) [ClassBio](#type-class-classbio-22732)
>
> **instance** HasField "code" [ClassBio](#type-class-classbio-22732) Text
>
> **instance** HasField "description" [ClassBio](#type-class-classbio-22732) Text
>
> **instance** HasField "title" [ClassBio](#type-class-classbio-22732) Text
>
> **instance** HasField "uid" [ClassBio](#type-class-classbio-22732) Int

<a name="type-class-classkey-47315"></a>**data** [ClassKey](#type-class-classkey-47315)

> A (registrar, uid) key for classes
>
> <a name="constr-class-classkey-65042"></a>[ClassKey](#constr-class-classkey-65042)
>
> > | Field     | Type      | Description |
> > | :-------- | :-------- | :---------- |
> > | registrar | Party     |  |
> > | uid       | Int       |  |
>
> **instance** Eq [ClassKey](#type-class-classkey-47315)
>
> **instance** Ord [ClassKey](#type-class-classkey-47315)
>
> **instance** Show [ClassKey](#type-class-classkey-47315)
>
> **instance** HasField "currClassKey" [ClassSwap](ClassSwap.html#type-classswap-classswap-72105) [ClassKey](#type-class-classkey-47315)
>
> **instance** HasField "have" [ClassTransfer](Cycle.html#type-cycle-classtransfer-9450) [ClassKey](#type-class-classkey-47315)
>
> **instance** HasField "registrar" [ClassKey](#type-class-classkey-47315) Party
>
> **instance** HasField "uid" [ClassKey](#type-class-classkey-47315) Int
>
> **instance** HasField "want" [ClassTransfer](Cycle.html#type-cycle-classtransfer-9450) [ClassKey](#type-class-classkey-47315)
>
> **instance** HasField "wantClassKey" [ClassSwap](ClassSwap.html#type-classswap-classswap-72105) [ClassKey](#type-class-classkey-47315)
>
> **instance** HasExerciseByKey [Class](#type-class-class-70181) [ClassKey](#type-class-classkey-47315) AddStudent (ContractId [Class](#type-class-class-70181))
>
> **instance** HasExerciseByKey [Class](#type-class-class-70181) [ClassKey](#type-class-classkey-47315) CloseRegistration (ContractId [Class](#type-class-class-70181))
>
> **instance** HasExerciseByKey [Class](#type-class-class-70181) [ClassKey](#type-class-classkey-47315) DropStudent (ContractId [Class](#type-class-class-70181))
>
> **instance** HasExerciseByKey [Class](#type-class-class-70181) [ClassKey](#type-class-classkey-47315) Archive ()
>
> **instance** HasFetchByKey [Class](#type-class-class-70181) [ClassKey](#type-class-classkey-47315)
>
> **instance** HasFromAnyContractKey [Class](#type-class-class-70181) [ClassKey](#type-class-classkey-47315)
>
> **instance** HasKey [Class](#type-class-class-70181) [ClassKey](#type-class-classkey-47315)
>
> **instance** HasLookupByKey [Class](#type-class-class-70181) [ClassKey](#type-class-classkey-47315)
>
> **instance** HasMaintainer [Class](#type-class-class-70181) [ClassKey](#type-class-classkey-47315)
>
> **instance** HasToAnyContractKey [Class](#type-class-class-70181) [ClassKey](#type-class-classkey-47315)
