.. _module-class-5316:

Module Class
============

Templates
---------

.. _type-class-class-70181:

**template** `Class <type-class-class-70181_>`_

  A Class Template

  Class contracts represent classes that exist for the current semester\.
  The registrar can create a class, swap students, finialize the registration, or archive it
  after the semester is over\.

  .. list-table::
     :widths: 15 10 30
     :header-rows: 1

     * - Field
       - Type
       - Description
     * - bio
       - `ClassBio <type-class-classbio-22732_>`_
       -
     * - registrar
       - Party
       -
     * - professor
       - Party
       -
     * - students
       - Set :ref:`Student <type-data-student-student-55208>`
       -
     * - grantedSwap
       - Set :ref:`Student <type-data-student-student-55208>`
       -
     * - finalized
       - Bool
       -

  + **Choice AddStudent**

    .. list-table::
       :widths: 15 10 30
       :header-rows: 1

       * - Field
         - Type
         - Description
       * - student
         - :ref:`Student <type-data-student-student-55208>`
         -
       * - fromTrade
         - Bool
         -

  + **Choice Archive**

    (no fields)

  + **Choice CloseRegistration**

    (no fields)

  + **Choice DropStudent**

    .. list-table::
       :widths: 15 10 30
       :header-rows: 1

       * - Field
         - Type
         - Description
       * - student
         - :ref:`Student <type-data-student-student-55208>`
         -

Data Types
----------

.. _type-class-classbio-22732:

**data** `ClassBio <type-class-classbio-22732_>`_

  A bio of a class that doesn't change
  across semesters

  .. _constr-class-classbio-58973:

  `ClassBio <constr-class-classbio-58973_>`_

    .. list-table::
       :widths: 15 10 30
       :header-rows: 1

       * - Field
         - Type
         - Description
       * - title
         - Text
         -
       * - description
         - Text
         -
       * - code
         - Text
         -
       * - uid
         - Int
         -

  **instance** Eq `ClassBio <type-class-classbio-22732_>`_

  **instance** Ord `ClassBio <type-class-classbio-22732_>`_

  **instance** Show `ClassBio <type-class-classbio-22732_>`_

  **instance** HasField \"bio\" `Class <type-class-class-70181_>`_ `ClassBio <type-class-classbio-22732_>`_

  **instance** HasField \"code\" `ClassBio <type-class-classbio-22732_>`_ Text

  **instance** HasField \"description\" `ClassBio <type-class-classbio-22732_>`_ Text

  **instance** HasField \"title\" `ClassBio <type-class-classbio-22732_>`_ Text

  **instance** HasField \"uid\" `ClassBio <type-class-classbio-22732_>`_ Int

.. _type-class-classkey-47315:

**data** `ClassKey <type-class-classkey-47315_>`_

  A (registrar, uid) key for classes

  .. _constr-class-classkey-65042:

  `ClassKey <constr-class-classkey-65042_>`_

    .. list-table::
       :widths: 15 10 30
       :header-rows: 1

       * - Field
         - Type
         - Description
       * - registrar
         - Party
         -
       * - uid
         - Int
         -

  **instance** Eq `ClassKey <type-class-classkey-47315_>`_

  **instance** Ord `ClassKey <type-class-classkey-47315_>`_

  **instance** Show `ClassKey <type-class-classkey-47315_>`_

  **instance** HasField \"currClassKey\" :ref:`ClassSwap <type-classswap-classswap-72105>` `ClassKey <type-class-classkey-47315_>`_

  **instance** HasField \"have\" :ref:`ClassTransfer <type-cycle-classtransfer-9450>` `ClassKey <type-class-classkey-47315_>`_

  **instance** HasField \"registrar\" `ClassKey <type-class-classkey-47315_>`_ Party

  **instance** HasField \"uid\" `ClassKey <type-class-classkey-47315_>`_ Int

  **instance** HasField \"want\" :ref:`ClassTransfer <type-cycle-classtransfer-9450>` `ClassKey <type-class-classkey-47315_>`_

  **instance** HasField \"wantClassKey\" :ref:`ClassSwap <type-classswap-classswap-72105>` `ClassKey <type-class-classkey-47315_>`_

  **instance** HasExerciseByKey `Class <type-class-class-70181_>`_ `ClassKey <type-class-classkey-47315_>`_ AddStudent (ContractId `Class <type-class-class-70181_>`_)

  **instance** HasExerciseByKey `Class <type-class-class-70181_>`_ `ClassKey <type-class-classkey-47315_>`_ CloseRegistration (ContractId `Class <type-class-class-70181_>`_)

  **instance** HasExerciseByKey `Class <type-class-class-70181_>`_ `ClassKey <type-class-classkey-47315_>`_ DropStudent (ContractId `Class <type-class-class-70181_>`_)

  **instance** HasExerciseByKey `Class <type-class-class-70181_>`_ `ClassKey <type-class-classkey-47315_>`_ Archive ()

  **instance** HasFetchByKey `Class <type-class-class-70181_>`_ `ClassKey <type-class-classkey-47315_>`_

  **instance** HasFromAnyContractKey `Class <type-class-class-70181_>`_ `ClassKey <type-class-classkey-47315_>`_

  **instance** HasKey `Class <type-class-class-70181_>`_ `ClassKey <type-class-classkey-47315_>`_

  **instance** HasLookupByKey `Class <type-class-class-70181_>`_ `ClassKey <type-class-classkey-47315_>`_

  **instance** HasMaintainer `Class <type-class-class-70181_>`_ `ClassKey <type-class-classkey-47315_>`_

  **instance** HasToAnyContractKey `Class <type-class-class-70181_>`_ `ClassKey <type-class-classkey-47315_>`_
