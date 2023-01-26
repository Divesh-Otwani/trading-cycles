.. _module-classswap-81723:

Module ClassSwap
================

Templates
---------

.. _type-classswap-classswap-72105:

**template** `ClassSwap <type-classswap-classswap-72105_>`_

  A contract affirming a student is authorized to swap
  one class for another and participate in cycle trades

  .. list-table::
     :widths: 15 10 30
     :header-rows: 1

     * - Field
       - Type
       - Description
     * - currClassKey
       - :ref:`ClassKey <type-class-classkey-47315>`
       -
     * - wantClassKey
       - :ref:`ClassKey <type-class-classkey-47315>`
       -
     * - student
       - :ref:`Student <type-data-student-student-55208>`
       -
     * - registrar
       - Party
       -
     * - currProfessor
       - Party
       -
     * - advisor
       - Party
       -

  + **Choice Archive**

    (no fields)

.. _type-classswap-classswappending-40631:

**template** `ClassSwapPending <type-classswap-classswappending-40631_>`_

  A contract to make a class swap once all the needed
  signatories have signed off\. It uses a mix of a propose\-accept
  and multi\-party\-agreement pattern\.

  .. list-table::
     :widths: 15 10 30
     :header-rows: 1

     * - Field
       - Type
       - Description
     * - swap
       - `ClassSwap <type-classswap-classswap-72105_>`_
       -
     * - currentSigners
       - Set Party
       -

  + **Choice Archive**

    (no fields)

  + **Choice ClassSwap\_Abort**

    .. list-table::
       :widths: 15 10 30
       :header-rows: 1

       * - Field
         - Type
         - Description
       * - party
         - Party
         -

  + **Choice ClassSwap\_Finalize**

    (no fields)

  + **Choice ClassSwap\_Sign**

    .. list-table::
       :widths: 15 10 30
       :header-rows: 1

       * - Field
         - Type
         - Description
       * - signer
         - Party
         -

Functions
---------

.. _function-classswap-validateswap-49294:

`validateSwap <function-classswap-validateswap-49294_>`_
  \: `ClassSwap <type-classswap-classswap-72105_>`_ \-\> Update Bool

  Validity conditions for making a swap contract\:
  Both classes exist as active, the professor matches the current class,
  the student is in the current class but not by a swap,
  the student is not in the other class, and both classes are not finalized\.
