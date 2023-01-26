.. _module-cycle-6218:

Module Cycle
============

Templates
---------

.. _type-cycle-cycle-39369:

**template** `Cycle <type-cycle-cycle-39369_>`_

  A Cycle of trades, that if valid can be performed

  .. list-table::
     :widths: 15 10 30
     :header-rows: 1

     * - Field
       - Type
       - Description
     * - transfers
       - \[`ClassTransfer <type-cycle-classtransfer-9450_>`_\]
       -
     * - matchingSwaps
       - Map `ClassTransfer <type-cycle-classtransfer-9450_>`_ (ContractId :ref:`ClassSwap <type-classswap-classswap-72105>`)
       -
     * - registrar
       - Party
       -

  + **Choice Archive**

    (no fields)

  + **Choice TryExecute**

    (no fields)

.. _type-cycle-cyclepending-36783:

**template** `CyclePending <type-cycle-cyclepending-36783_>`_

  A contract for making a cycle once each
  ClassTransfer has a corresponding ContractId ClassSwap
  and all the signatories have been added to haveSigned
  (including the registrar)

  .. list-table::
     :widths: 15 10 30
     :header-rows: 1

     * - Field
       - Type
       - Description
     * - cycle
       - `Cycle <type-cycle-cycle-39369_>`_
       -
     * - haveSigned
       - Set Party
       -

  + **Choice Archive**

    (no fields)

  + **Choice CyclePending\_Abort**

    .. list-table::
       :widths: 15 10 30
       :header-rows: 1

       * - Field
         - Type
         - Description
       * - party
         - Party
         -

  + **Choice CyclePending\_Finalize**

    (no fields)

  + **Choice CyclePending\_RegistrarSign**

    (no fields)

  + **Choice CyclePending\_TransferSign**

    .. list-table::
       :widths: 15 10 30
       :header-rows: 1

       * - Field
         - Type
         - Description
       * - witness
         - `TransferWitness <type-cycle-transferwitness-69795_>`_
         -

Data Types
----------

.. _type-cycle-classtransfer-9450:

**data** `ClassTransfer <type-cycle-classtransfer-9450_>`_

  A lightweight represenation of a student's
  transfer of losing a class they have and gaining
  a class they want

  .. _constr-cycle-classtransfer-61329:

  `ClassTransfer <constr-cycle-classtransfer-61329_>`_

    .. list-table::
       :widths: 15 10 30
       :header-rows: 1

       * - Field
         - Type
         - Description
       * - student
         - :ref:`Student <type-data-student-student-55208>`
         -
       * - have
         - :ref:`ClassKey <type-class-classkey-47315>`
         -
       * - want
         - :ref:`ClassKey <type-class-classkey-47315>`
         -

  **instance** Eq `ClassTransfer <type-cycle-classtransfer-9450_>`_

  **instance** Ord `ClassTransfer <type-cycle-classtransfer-9450_>`_

  **instance** Show `ClassTransfer <type-cycle-classtransfer-9450_>`_

  **instance** HasField \"have\" `ClassTransfer <type-cycle-classtransfer-9450_>`_ :ref:`ClassKey <type-class-classkey-47315>`

  **instance** HasField \"matchingSwaps\" `Cycle <type-cycle-cycle-39369_>`_ (Map `ClassTransfer <type-cycle-classtransfer-9450_>`_ (ContractId :ref:`ClassSwap <type-classswap-classswap-72105>`))

  **instance** HasField \"student\" `ClassTransfer <type-cycle-classtransfer-9450_>`_ :ref:`Student <type-data-student-student-55208>`

  **instance** HasField \"transfer\" `TransferWitness <type-cycle-transferwitness-69795_>`_ `ClassTransfer <type-cycle-classtransfer-9450_>`_

  **instance** HasField \"transfers\" `Cycle <type-cycle-cycle-39369_>`_ \[`ClassTransfer <type-cycle-classtransfer-9450_>`_\]

  **instance** HasField \"want\" `ClassTransfer <type-cycle-classtransfer-9450_>`_ :ref:`ClassKey <type-class-classkey-47315>`

.. _type-cycle-transferwitness-69795:

**data** `TransferWitness <type-cycle-transferwitness-69795_>`_

  A witness by which a ClassTransfer is validated
  This is not checked upon adding it to a cycle, but on executing

  .. _constr-cycle-transferwitness-72100:

  `TransferWitness <constr-cycle-transferwitness-72100_>`_

    .. list-table::
       :widths: 15 10 30
       :header-rows: 1

       * - Field
         - Type
         - Description
       * - swapId
         - ContractId :ref:`ClassSwap <type-classswap-classswap-72105>`
         -
       * - transfer
         - `ClassTransfer <type-cycle-classtransfer-9450_>`_
         -

  **instance** Eq `TransferWitness <type-cycle-transferwitness-69795_>`_

  **instance** Ord `TransferWitness <type-cycle-transferwitness-69795_>`_

  **instance** Show `TransferWitness <type-cycle-transferwitness-69795_>`_

  **instance** HasField \"swapId\" `TransferWitness <type-cycle-transferwitness-69795_>`_ (ContractId :ref:`ClassSwap <type-classswap-classswap-72105>`)

  **instance** HasField \"transfer\" `TransferWitness <type-cycle-transferwitness-69795_>`_ `ClassTransfer <type-cycle-classtransfer-9450_>`_

  **instance** HasField \"witness\" CyclePending\_TransferSign `TransferWitness <type-cycle-transferwitness-69795_>`_

Functions
---------

.. _function-cycle-swappairvalid-79994:

`swapPairValid <function-cycle-swappairvalid-79994_>`_
  \: Party \-\> (`ClassTransfer <type-cycle-classtransfer-9450_>`_, ContractId :ref:`ClassSwap <type-classswap-classswap-72105>`) \-\> Update ()

  Check that the swap exists, that it matches the transfer by the (want, have,
  student) fields, that the registrar is the one in the cycle, and that the swap
  has it's own integrity (see @ClassSwap\.validateSwap@)\.

.. _function-cycle-executecycle-47293:

`executeCycle <function-cycle-executecycle-47293_>`_
  \: \[`ClassTransfer <type-cycle-classtransfer-9450_>`_\] \-\> Update ()

  Drop and add classes according to the transfers,
  failing if the class state has changed in the meantime

.. _function-cycle-partiesoftransfers-3799:

`partiesOfTransfers <function-cycle-partiesoftransfers-3799_>`_
  \: \[`ClassTransfer <type-cycle-classtransfer-9450_>`_\] \-\> Set Party

  Get all the students parties in a list of class transfers

.. _function-cycle-validtransfercycle-2329:

`validTransferCycle <function-cycle-validtransfercycle-2329_>`_
  \: \[`ClassTransfer <type-cycle-classtransfer-9450_>`_\] \-\> Bool

  A predicate on making sure a list of class transfers is valid
  in all properties

.. _function-cycle-transfersformcycle-28314:

`transfersFormCycle <function-cycle-transfersformcycle-28314_>`_
  \: \[`ClassTransfer <type-cycle-classtransfer-9450_>`_\] \-\> Bool

  Cycle order validity
  It's in order in a line and for (end \:\: \.\.\. \:\: start \:\: \[\])
  we have end\.have \=\= start\.want

.. _function-cycle-transfersformchain-73223:

`transfersFormChain <function-cycle-transfersformchain-73223_>`_
  \: \[`ClassTransfer <type-cycle-classtransfer-9450_>`_\] \-\> Bool

  Linear order validity
  (x \:\: y \:\: xs) means x\.want \=\= y\.have

.. _function-cycle-uniqueclasses-83500:

`uniqueClasses <function-cycle-uniqueclasses-83500_>`_
  \: \[`ClassTransfer <type-cycle-classtransfer-9450_>`_\] \-\> Bool

  All classes are unique so the cycle can't be
  short\-circuited
