The code is well documented and easily readable

Functionally, everything works correctly.

No good reason for creditModifier to be a global variable.

What should have been documented is the way the program assigns the credit modifier to
personal codes based on the last 4 digits. As of now this mechanism has to be discovered
by inspecting the source code.

The method DecisionEngine.calculateApprovedLoan catches the exceptions thrown by verifyInputs
and proceeds with returning a decision with an error message, which is bad and completely
unnecessary provided that it is already specified that calculateApprovedLoan throws those
exceptions which are later handled in the controller. That way the controller also fails to
respond with "bad request". This seems to be the only such case and also the only case where
the errorMessage field in the Decision class is assigned and used. Therefore, this field
is redundant and should be removed.