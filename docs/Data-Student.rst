.. _module-data-student-28646:

Module Data.Student
===================

Data Types
----------

.. _type-data-student-student-55208:

**data** `Student <type-data-student-student-55208_>`_

  .. _constr-data-student-student-97081:

  `Student <constr-data-student-student-97081_>`_

    .. list-table::
       :widths: 15 10 30
       :header-rows: 1

       * - Field
         - Type
         - Description
       * - name
         - Text
         -
       * - party
         - Party
         -

  **instance** Eq `Student <type-data-student-student-55208_>`_

  **instance** Ord `Student <type-data-student-student-55208_>`_

  **instance** Show `Student <type-data-student-student-55208_>`_

  **instance** HasField \"grantedSwap\" :ref:`Class <type-class-class-70181>` (Set `Student <type-data-student-student-55208_>`_)

  **instance** HasField \"name\" `Student <type-data-student-student-55208_>`_ Text

  **instance** HasField \"party\" `Student <type-data-student-student-55208_>`_ Party

  **instance** HasField \"student\" AddStudent `Student <type-data-student-student-55208_>`_

  **instance** HasField \"student\" DropStudent `Student <type-data-student-student-55208_>`_

  **instance** HasField \"student\" :ref:`ClassSwap <type-classswap-classswap-72105>` `Student <type-data-student-student-55208_>`_

  **instance** HasField \"student\" :ref:`ClassTransfer <type-cycle-classtransfer-9450>` `Student <type-data-student-student-55208_>`_

  **instance** HasField \"students\" :ref:`Class <type-class-class-70181>` (Set `Student <type-data-student-student-55208_>`_)
