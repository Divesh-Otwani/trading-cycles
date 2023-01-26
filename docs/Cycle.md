# <a name="module-cycle-6218"></a>Module Cycle

## Templates

<a name="type-cycle-cycle-39369"></a>**template** [Cycle](#type-cycle-cycle-39369)

> A Cycle of trades, that if valid can be performed
>
> | Field                                                                                                                       | Type                                                                                                                        | Description |
> | :-------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------- | :---------- |
> | transfers                                                                                                                   | \[[ClassTransfer](#type-cycle-classtransfer-9450)\]                                                                         |  |
> | matchingSwaps                                                                                                               | Map [ClassTransfer](#type-cycle-classtransfer-9450) (ContractId [ClassSwap](ClassSwap.html#type-classswap-classswap-72105)) |  |
> | registrar                                                                                                                   | Party                                                                                                                       |  |
>
> * **Choice Archive**
>
>   (no fields)
>
> * **Choice TryExecute**
>
>   (no fields)

<a name="type-cycle-cyclepending-36783"></a>**template** [CyclePending](#type-cycle-cyclepending-36783)

> A contract for making a cycle once each
> ClassTransfer has a corresponding ContractId ClassSwap
> and all the signatories have been added to haveSigned
> (including the registrar)
>
> | Field                            | Type                             | Description |
> | :------------------------------- | :------------------------------- | :---------- |
> | cycle                            | [Cycle](#type-cycle-cycle-39369) |  |
> | haveSigned                       | Set Party                        |  |
>
> * **Choice Archive**
>
>   (no fields)
>
> * **Choice CyclePending\_Abort**
>
>   | Field | Type  | Description |
>   | :---- | :---- | :---------- |
>   | party | Party |  |
>
> * **Choice CyclePending\_Finalize**
>
>   (no fields)
>
> * **Choice CyclePending\_RegistrarSign**
>
>   (no fields)
>
> * **Choice CyclePending\_TransferSign**
>
>   | Field                                                | Type                                                 | Description |
>   | :--------------------------------------------------- | :--------------------------------------------------- | :---------- |
>   | witness                                              | [TransferWitness](#type-cycle-transferwitness-69795) |  |

## Data Types

<a name="type-cycle-classtransfer-9450"></a>**data** [ClassTransfer](#type-cycle-classtransfer-9450)

> A lightweight represenation of a student's
> transfer of losing a class they have and gaining
> a class they want
>
> <a name="constr-cycle-classtransfer-61329"></a>[ClassTransfer](#constr-cycle-classtransfer-61329)
>
> > | Field                                                        | Type                                                         | Description |
> > | :----------------------------------------------------------- | :----------------------------------------------------------- | :---------- |
> > | student                                                      | [Student](Data-Student.html#type-data-student-student-55208) |  |
> > | have                                                         | [ClassKey](Class.html#type-class-classkey-47315)             |  |
> > | want                                                         | [ClassKey](Class.html#type-class-classkey-47315)             |  |
>
> **instance** Eq [ClassTransfer](#type-cycle-classtransfer-9450)
>
> **instance** Ord [ClassTransfer](#type-cycle-classtransfer-9450)
>
> **instance** Show [ClassTransfer](#type-cycle-classtransfer-9450)
>
> **instance** HasField "have" [ClassTransfer](#type-cycle-classtransfer-9450) [ClassKey](Class.html#type-class-classkey-47315)
>
> **instance** HasField "matchingSwaps" [Cycle](#type-cycle-cycle-39369) (Map [ClassTransfer](#type-cycle-classtransfer-9450) (ContractId [ClassSwap](ClassSwap.html#type-classswap-classswap-72105)))
>
> **instance** HasField "student" [ClassTransfer](#type-cycle-classtransfer-9450) [Student](Data-Student.html#type-data-student-student-55208)
>
> **instance** HasField "transfer" [TransferWitness](#type-cycle-transferwitness-69795) [ClassTransfer](#type-cycle-classtransfer-9450)
>
> **instance** HasField "transfers" [Cycle](#type-cycle-cycle-39369) \[[ClassTransfer](#type-cycle-classtransfer-9450)\]
>
> **instance** HasField "want" [ClassTransfer](#type-cycle-classtransfer-9450) [ClassKey](Class.html#type-class-classkey-47315)

<a name="type-cycle-transferwitness-69795"></a>**data** [TransferWitness](#type-cycle-transferwitness-69795)

> A witness by which a ClassTransfer is validated
> This is not checked upon adding it to a cycle, but on executing
>
> <a name="constr-cycle-transferwitness-72100"></a>[TransferWitness](#constr-cycle-transferwitness-72100)
>
> > | Field                                                                 | Type                                                                  | Description |
> > | :-------------------------------------------------------------------- | :-------------------------------------------------------------------- | :---------- |
> > | swapId                                                                | ContractId [ClassSwap](ClassSwap.html#type-classswap-classswap-72105) |  |
> > | transfer                                                              | [ClassTransfer](#type-cycle-classtransfer-9450)                       |  |
>
> **instance** Eq [TransferWitness](#type-cycle-transferwitness-69795)
>
> **instance** Ord [TransferWitness](#type-cycle-transferwitness-69795)
>
> **instance** Show [TransferWitness](#type-cycle-transferwitness-69795)
>
> **instance** HasField "swapId" [TransferWitness](#type-cycle-transferwitness-69795) (ContractId [ClassSwap](ClassSwap.html#type-classswap-classswap-72105))
>
> **instance** HasField "transfer" [TransferWitness](#type-cycle-transferwitness-69795) [ClassTransfer](#type-cycle-classtransfer-9450)
>
> **instance** HasField "witness" CyclePending\_TransferSign [TransferWitness](#type-cycle-transferwitness-69795)

## Functions

<a name="function-cycle-swappairvalid-79994"></a>[swapPairValid](#function-cycle-swappairvalid-79994)

> : Party -\> ([ClassTransfer](#type-cycle-classtransfer-9450), ContractId [ClassSwap](ClassSwap.html#type-classswap-classswap-72105)) -\> Update ()
>
> Check that the swap exists, that it matches the transfer by the (want, have,
> student) fields, that the registrar is the one in the cycle, and that the swap
> has it's own integrity (see @ClassSwap.validateSwap@).

<a name="function-cycle-executecycle-47293"></a>[executeCycle](#function-cycle-executecycle-47293)

> : \[[ClassTransfer](#type-cycle-classtransfer-9450)\] -\> Update ()
>
> Drop and add classes according to the transfers,
> failing if the class state has changed in the meantime

<a name="function-cycle-partiesoftransfers-3799"></a>[partiesOfTransfers](#function-cycle-partiesoftransfers-3799)

> : \[[ClassTransfer](#type-cycle-classtransfer-9450)\] -\> Set Party
>
> Get all the students parties in a list of class transfers

<a name="function-cycle-validtransfercycle-2329"></a>[validTransferCycle](#function-cycle-validtransfercycle-2329)

> : \[[ClassTransfer](#type-cycle-classtransfer-9450)\] -\> Bool
>
> A predicate on making sure a list of class transfers is valid
> in all properties

<a name="function-cycle-transfersformcycle-28314"></a>[transfersFormCycle](#function-cycle-transfersformcycle-28314)

> : \[[ClassTransfer](#type-cycle-classtransfer-9450)\] -\> Bool
>
> Cycle order validity
> It's in order in a line and for (end :: ... :: start :: [])
> we have end.have == start.want

<a name="function-cycle-transfersformchain-73223"></a>[transfersFormChain](#function-cycle-transfersformchain-73223)

> : \[[ClassTransfer](#type-cycle-classtransfer-9450)\] -\> Bool
>
> Linear order validity
> (x :: y :: xs) means x.want == y.have

<a name="function-cycle-uniqueclasses-83500"></a>[uniqueClasses](#function-cycle-uniqueclasses-83500)

> : \[[ClassTransfer](#type-cycle-classtransfer-9450)\] -\> Bool
>
> All classes are unique so the cycle can't be
> short-circuited
