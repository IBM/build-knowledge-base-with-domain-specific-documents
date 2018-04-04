Tips for Developers
===================

The notebook is designed to be run top-down. Settings in early cells are used
in later cells. Some variables are also cleared to free up memory. So, although
you can often run single cell repeatedly while testing changes, you may want
to start over from the top if anything seems to be missing.

Setting credentials
-------------------
Credentials need to be added to the notebook to access some IBM Cloud services.
The credentials are set near the top of the notebook to make it
more obvious that they need to be set and also to make it more obvious that
you will be saving a notebook with credentials. You should not share your
notebook with anyone that you would not share your credentials with
unless you use the ``share`` feature with the ``Only text and output`` or
``All content excluding sensitive code cells`` option.

The ```@hidden_cell``` magic is used to mark the credentials cells as
"sensitive". If you do any rearranging of sensitive code, remember to identify
sensitive cells with ``@hidden_cell``.

Installing Python packages
--------------------------
A notebook can use ```!pip install``` to install the Python packages
from PyPI. You can follow this example if you decide to use additional Python
packages in your notebook. Check the output to see that the install was
successful. See the "Controlling output" section below for more information on
how to suppress/show the output. You might want to use ``DEBUG = True`` until
you've verified that the pip install was successful.

> **Note**:  After running a cell with pip install, you may need to restart
the kernel and then run the cells again from the top.

Importing libraries
-------------------
Import and some setup of libraries is done near the top. This is another
example of why cells need to run top-down. Keeping the imports near the top
is a Python PEP8 style convention. Python does not require this convention,
but Python developers are used to looking for imports at the top.

Defining global variables and helper functions
----------------------------------------------
After the imports, a few global variables and helper functions are defined.
These allow for code re-use. These cells need to run before other cells can
use the functions and globals. These values do not change. You can change
and run the later cells over and over without always restarting from the top.

Controlling output
------------------
One of the great things about notebooks is that you can use them to document
what you are doing, show your work, show the results, and document your
conclusion -- all in one place. Sharing "your work" (the code) is a great
feature, but to make the "only text and output" web page look nice and clean
you can use the following tips.

#### @hidden_cell magic

The @hidden_cell magic is used to mark the credentials cells as "sensitive".
If you do any rearranging of sensitive code, remember to identify sensitive
cells with @hidden_cell.

#### Ending with a semi-colon

Statements in a notebook can end with a semi-colon. It looks like
bad Python, but it is actually a trick to prevent these statements from
showing their result in the output.

#### if DEBUG

A DEBUG boolean and 'if' statements can be used throughout the notebook
wherever some print statements are handy during development and might be
handy in the future, but are not something you want to share in the final
output.

#### %%capture captured_io

"%%capture captured_io" magic can be used to capture the output when nothing
else works. You can use that to hide the "!pip install" output and add a cell
right after it that will print the captured output if DEBUG is True.
