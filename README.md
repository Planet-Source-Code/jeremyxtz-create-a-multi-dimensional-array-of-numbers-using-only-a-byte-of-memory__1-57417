<div align="center">

## Create a multi\-dimensional array of numbers using only a byte of memory


</div>

### Description

Yes - REALLY!
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[jeremyxtz](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/jeremyxtz.md)
**Level**          |Advanced
**User Rating**    |4.0 (16 globes from 4 users)
**Compatibility**  |VB 5\.0, VB 6\.0
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__1-1.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/jeremyxtz-create-a-multi-dimensional-array-of-numbers-using-only-a-byte-of-memory__1-57417/archive/master.zip)





### Source Code

```
'create a multi-dimensional array of numbers using only a byte of memory
'We SHOULD all be familiar with using bits in a byte
'or integer to represent on/off values instead of booleans
'In fact we can use a variable (they're ALL just bytes)
'to represent any data we choose so long it has sufficient bits
'all we need do is write the code to access the variable appropriately
'This example uses a singe byte as a
'2 x 2 array of numbers of value 0-3
'using an integer array this would require
'20 bytes for the array
'+ (2 * 4) for the two dimensions
'+ (2 * 4) for the data
'= 36 bytes.
'We've used 1 !!
'The bits needn't represent 0-3 they can represent
'any four number range or four values
'A slightly more complex example would be a
'noughts and crosses(tic-tac-toe) game
'where there are 3 values -
'not filled, nought, cross
'this needs 2 bits (as in my example)
'there are 9 squares in a 3 x 3 grid =18 bits total
'which we could comfortably code in a long variable
'if your computer was trying to play
'a million tic-tac-toes games with you at once
'you'd save quite a few bits of memory
Private Sub Form_Load()
Dim exampleByte As Byte
setValue exampleByte, 0, 0, 3
setValue exampleByte, 0, 1, 2
setValue exampleByte, 1, 0, 1
setValue exampleByte, 1, 1, 0
MsgBox getValue(exampleByte, 0, 0)
MsgBox getValue(exampleByte, 0, 1)
MsgBox getValue(exampleByte, 1, 0)
MsgBox getValue(exampleByte, 1, 1)
End Sub
Sub setValue(b As Byte, ByVal x As Integer, ByVal y As Integer, value)
Adjust = getAdjust(x, y)
If Adjust = 0 Then
b = b And Not 3 'clear the old value
b = b Or value 'write the new one
Else
b = b And Not (Adjust * 3)
b = b Or (Adjust * value)
End If
End Sub
Function getValue(ByVal b As Byte, ByVal x As Integer, ByVal y As Integer) As Integer
Adjust = getAdjust(x, y)
If Adjust <> 0 Then b = b \ Adjust
getValue = b And Not 252 'simple masking of values
End Function
Function getAdjust(ByVal x As Integer, ByVal y As Integer) As Integer
'adjustment required to access correct row
If x <> 0 Then
getAdjust = x * 4
If y <> 0 Then getAdjust = (y * 16) * getAdjust
Else
getAdjust = y * 16
End If
End Function
```

