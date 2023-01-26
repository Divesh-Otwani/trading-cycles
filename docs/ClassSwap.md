# <a name="module-classswap-81723"></a>Module ClassSwap

## Templates

<a name="type-classswap-classswap-72105"></a>**template** [ClassSwap](#type-classswap-classswap-72105)

> A contract affirming a student is authorized to swap
> one class for another and participate in cycle trades
>
> | Field                                                        | Type                                                         | Description |
> | :----------------------------------------------------------- | :----------------------------------------------------------- | :---------- |
> | currClassKey                                                 | [ClassKey](Class.html#type-class-classkey-47315)             |  |
> | wantClassKey                                                 | [ClassKey](Class.html#type-class-classkey-47315)             |  |
> | student                                                      | [Student](Data-Student.html#type-data-student-student-55208) |  |
> | registrar                                                    | Party                                                        |  |
> | currProfessor                                                | Party                                                        |  |
> | advisor                                                      | Party                                                        |  |
>
> * **Choice Archive**
>
>   (no fields)

<a name="type-classswap-classswappending-40631"></a>**template** [ClassSwapPending](#type-classswap-classswappending-40631)

> A contract to make a class swap once all the needed
> signatories have signed off. It uses a mix of a propose-accept
> and multi-party-agreement pattern.
>
> | Field                                        | Type                                         | Description |
> | :------------------------------------------- | :------------------------------------------- | :---------- |
> | swap                                         | [ClassSwap](#type-classswap-classswap-72105) |  |
> | currentSigners                               | Set Party                                    |  |
>
> * **Choice Archive**
>
>   (no fields)
>
> * **Choice ClassSwap\_Abort**
>
>   | Field | Type  | Description |
>   | :---- | :---- | :---------- |
>   | party | Party |  |
>
> * **Choice ClassSwap\_Finalize**
>
>   (no fields)
>
> * **Choice ClassSwap\_Sign**
>
>   | Field  | Type   | Description |
>   | :----- | :----- | :---------- |
>   | signer | Party  |  |

## Functions

<a name="function-classswap-validateswap-49294"></a>[validateSwap](#function-classswap-validateswap-49294)

> : [ClassSwap](#type-classswap-classswap-72105) -\> Update Bool
>
> Validity conditions for making a swap contract:
> Both classes exist as active, the professor matches the current class,
> the student is in the current class but not by a swap,
> the student is not in the other class, and both classes are not finalized.
