<div align="center">

## THE BEST\! 36 Different Gradient Effects and Unlimited Colors


</div>

### Description

So many effects that I can't have a small enough picture for them all! Check it out for unlimited colors and 36 different effects(Including some you've never seen). Please Vote! I am working on turning this into an ActiveX control.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[CoDe ReD CrYsTaL](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/code-red-crystal.md)
**Level**          |Advanced
**User Rating**    |5.0 (20 globes from 4 users)
**Compatibility**  |VB 6\.0
**Category**       |[Graphics](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/graphics__1-46.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/code-red-crystal-the-best-36-different-gradient-effects-and-unlimited-colors__1-29686/archive/master.zip)





### Source Code

```
'The current color posistion
Dim FadeNumPos As Integer
'The First RGB Values
Dim R1 As Integer, G1 As Integer, B1 As Integer
'The Second RGB Values
Dim R2 As Integer, G2 As Integer, B2 As Integer
'These are the RGB values for the current line
Dim NewRed As Integer, NewGreen As Integer, NewBlue As Integer
'Easier than an array to store a color
Public FadeColors As New Collection
'The Difference
Dim OverAllDiff
'This is the long value for the line color
Dim NewColor
'Gets the colors ready to draw the line
'Then calls on the effect sub to make the gradient
Public Function Gradeffect(Target As Object, style As Integer)
  'Clear the object
  Target.Cls
  'Get the fade count
  FadeTimes = FadeColors.Count - 1
  'Set the draw width for the line
  Target.DrawWidth = 1
  'Want auto redraw
  Target.AutoRedraw = True
  'Don't Modify these. Won't work without them
  Target.ScaleWidth = 255 'No modifying
  Target.ScaleHeight = Target.ScaleWidth 'No modifying
  'do each color
  For FadeNumPos = 1 To FadeTimes
    'Set the Start values
    R1 = R2
    G1 = G2
    B1 = B2
    'Set the Start values for the first color
    If FadeNumPos = 1 Then
      R1 = FadeColors(1) Mod &H100
      G1 = (FadeColors(1) \ &H100) Mod &H100
      B1 = (FadeColors(1) \ &H10000) Mod &H100
    End If
    'Set the End values
    R2 = FadeColors(FadeNumPos + 1) Mod &H100
    G2 = (FadeColors(FadeNumPos + 1) \ &H100) Mod &H100
    B2 = (FadeColors(FadeNumPos + 1) \ &H10000) Mod &H100
    'Get the differences
    RedDiff = (R1 - R2) / Target.ScaleHeight * FadeTimes
    GreenDiff = (G1 - G2) / Target.ScaleHeight * FadeTimes
    BlueDiff = (B1 - B2) / Target.ScaleHeight * FadeTimes
    'For each line
    For OverAllDiff = ((FadeNumPos - 1) * Target.ScaleWidth / FadeTimes) To (FadeNumPos * Target.ScaleHeight / FadeTimes)
      'Get the new RGB values
      NewRed = R1 - RedDiff * (OverAllDiff - ((FadeNumPos - 1) * Target.ScaleWidth / FadeTimes))
      NewGreen = G1 - GreenDiff * (OverAllDiff - ((FadeNumPos - 1) * Target.ScaleWidth / FadeTimes))
      NewBlue = B1 - BlueDiff * (OverAllDiff - ((FadeNumPos - 1) * Target.ScaleWidth / FadeTimes))
      'Set the color
      NewColor = RGB(NewRed, NewGreen, NewBlue)
      'Do the effect
      Effect Target, style
    'Next Line
    Next
  'Next color
  Next
'Done here
End Function
'The effect
Function Effect(Target As Object, kind As Integer)
  'There are 36 different gradients. Try them all
  Select Case kind
    'Clockwork Down - Cool and New
    Case 1
    Target.Line (OverAllDiff + 1, Target.ScaleHeight)-(Target.ScaleWidth - OverAllDiff, OverAllDiff), NewColor, BF
    'Clockwork Left - Cool and new!
    Case 2
    Target.Line (0, Target.ScaleWidth - OverAllDiff)-(Target.ScaleWidth - OverAllDiff, OverAllDiff), NewColor, BF
    'Clockwork Up - Cool and new
    Case 3
    Target.Line (OverAllDiff, Target.ScaleHeight - OverAllDiff)-(Target.ScaleHeight, 0), NewColor, BF
    'Clockwork Right
    Case 4
    Target.Line (OverAllDiff, Target.ScaleHeight - OverAllDiff)-(Target.ScaleHeight, OverAllDiff), NewColor, BF
    'Right to Left
    Case 5
    Target.Line (Target.ScaleWidth - OverAllDiff, 0)-(Target.ScaleWidth - OverAllDiff, Target.ScaleHeight - 20), NewColor, BF
    'Left to Right
    Case 6
    Target.Line (OverAllDiff, 0)-(OverAllDiff + 1, Target.ScaleWidth), NewColor, BF
    'Fade Out from bottom right
    Case 7
    Target.Line (0, Target.ScaleHeight - OverAllDiff)-(Target.ScaleWidth, Target.ScaleHeight - (OverAllDiff + 1)), NewColor, BF
    Target.Line (Target.ScaleWidth - OverAllDiff, 0)-(Target.ScaleWidth - (OverAllDiff + 1), Target.ScaleHeight), NewColor, BF
    'Fade Out from bottom left
    Case 8
    Target.Line (0, Target.ScaleHeight - OverAllDiff)-(Target.ScaleWidth, Target.ScaleHeight - (OverAllDiff + 1)), NewColor, BF
    Target.Line (OverAllDiff, 0)-(OverAllDiff + 1, Target.ScaleHeight), NewColor, BF
    'Fade Out from top left
    Case 9
    Target.Line (0, OverAllDiff)-(Target.ScaleWidth, OverAllDiff + 1), NewColor, BF
    Target.Line (OverAllDiff, 0)-(OverAllDiff + 1, Target.ScaleHeight), NewColor, BF
    'Fade Out from top right
    Case 10
    Target.Line (0, OverAllDiff)-(Target.ScaleWidth, OverAllDiff + 1), NewColor, BF
    Target.Line (Target.ScaleWidth - OverAllDiff, 0)-(Target.ScaleWidth - OverAllDiff, Target.ScaleHeight - 20), NewColor, BF
    'Fade Out from center
    Case 11
    Target.Line (Int(Target.ScaleWidth / 2 - OverAllDiff / 2), Int(Target.ScaleHeight / 2 - OverAllDiff / 2))-(Target.ScaleWidth / 2 + OverAllDiff / 2, Target.ScaleHeight / 2 + OverAllDiff / 2), NewColor, B
    'Fade In from bottom right
    Case 12
    Target.Line (OverAllDiff, Target.ScaleWidth)-(Target.ScaleWidth, OverAllDiff + 1), NewColor, BF
    'Fade In from bottom left
    Case 13
    Target.Line (0, Target.ScaleHeight)-(Target.ScaleWidth - OverAllDiff, OverAllDiff), NewColor, BF
    'Fade In from top left
    Case 14
    Target.Line (0, 0)-(Target.ScaleWidth - OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    'Fade In from top right
    Case 15
    Target.Line (Target.ScaleWidth, 0)-(OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    'Boxes 1
    Case 16
    Target.Line (Target.ScaleWidth, 0)-(OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    Target.Line (0, Target.ScaleHeight)-(Target.ScaleWidth - OverAllDiff, OverAllDiff), NewColor, BF
    'Boxes 2
    Case 17
    Target.Line (Target.ScaleWidth, 0)-(OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    Target.Line (OverAllDiff, Target.ScaleWidth)-(Target.ScaleWidth, OverAllDiff + 1), NewColor, BF
    'Boxes 3
    Case 18
    Target.Line (Target.ScaleWidth, 0)-(OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    Target.Line (0, Target.ScaleHeight)-(Target.ScaleWidth - OverAllDiff, OverAllDiff), NewColor, BF
    Target.Line (OverAllDiff, Target.ScaleWidth)-(Target.ScaleWidth, OverAllDiff + 1), NewColor, BF
    'Boxes 4
    Case 19
    Target.Line (0, Target.ScaleHeight)-(Target.ScaleWidth - OverAllDiff, OverAllDiff), NewColor, BF
    Target.Line (OverAllDiff, Target.ScaleWidth)-(Target.ScaleWidth, OverAllDiff + 1), NewColor, BF
    'Boxes 5
    Case 20
    Target.Line (Target.ScaleWidth, 0)-(OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    Target.Line (0, 0)-(Target.ScaleWidth - OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    'Boxes 6
    Case 21
    Target.Line (0, Target.ScaleHeight)-(Target.ScaleWidth - OverAllDiff, OverAllDiff), NewColor, BF
    Target.Line (0, 0)-(Target.ScaleWidth - OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    'Boxes 7
    Case 22
    Target.Line (OverAllDiff, Target.ScaleWidth)-(Target.ScaleWidth, OverAllDiff + 1), NewColor, BF
    Target.Line (0, 0)-(Target.ScaleWidth - OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    'Boxes 8
    Case 23
    Target.Line (0, 0)-(Target.ScaleWidth - OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    Target.Line (Target.ScaleWidth, 0)-(OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    Target.Line (0, Target.ScaleHeight)-(Target.ScaleWidth - OverAllDiff, OverAllDiff), NewColor, BF
    Target.Line (OverAllDiff, Target.ScaleWidth)-(Target.ScaleWidth, OverAllDiff + 1), NewColor, BF
    'Top to Bottom
    Case 24
    Target.Line (0, OverAllDiff)-(Target.ScaleWidth, OverAllDiff + 1), NewColor, BF
    'Bottom to Top
    Case 25
    Target.Line (0, 0)-(Target.ScaleWidth, Target.ScaleHeight - OverAllDiff), NewColor, BF
    'Refraction
    Case 26
    Target.Line (Target.ScaleWidth - OverAllDiff, OverAllDiff)-(Target.ScaleWidth - OverAllDiff, Target.ScaleHeight), NewColor, BF
    Target.Line (OverAllDiff, Target.ScaleHeight - OverAllDiff)-(Target.ScaleHeight, OverAllDiff), NewColor, BF
    'Line through middle
    Case 27
    Target.Line ((Target.ScaleWidth / 2) - (OverAllDiff / 2), 0)-((Target.ScaleWidth / 2) - (OverAllDiff / 2), Target.ScaleHeight), NewColor, BF
    Target.Line ((Target.ScaleWidth / 2) + (OverAllDiff / 2), 0)-((Target.ScaleWidth / 2) + (OverAllDiff / 2), Target.ScaleHeight), NewColor, BF
    'Exploded
    Case 28
    Target.Line (Target.ScaleWidth, OverAllDiff / 2)-(OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    Target.Line (0, Target.ScaleHeight)-(Target.ScaleWidth - OverAllDiff, OverAllDiff), NewColor, BF
    'Pouring
    Case 29
    Target.Line (Target.ScaleWidth, 0)-(OverAllDiff, Target.ScaleHeight), NewColor, BF
    Target.Line (0, Target.ScaleHeight)-(Target.ScaleWidth - OverAllDiff, OverAllDiff), NewColor, BF
    'lighthouse
    Case 30
    Target.Line (Target.ScaleWidth, OverAllDiff / 2)-(OverAllDiff, Target.ScaleHeight - OverAllDiff), NewColor, BF
    'Square
    Case 31
    Target.Line (OverAllDiff / 2, Target.ScaleWidth)-(Target.ScaleWidth, OverAllDiff + 1), NewColor, BF
    'Ripped
    Case 32
    Target.Line ((Target.ScaleHeight * OverAllDiff), OverAllDiff)-(OverAllDiff, Target.ScaleWidth + OverAllDiff), NewColor, BF
    'Prism
    Case 33
    Target.Line (Target.ScaleWidth - OverAllDiff, OverAllDiff)-(Target.ScaleWidth - OverAllDiff, Target.ScaleHeight), NewColor, BF
    Target.Line (OverAllDiff, Target.ScaleHeight - OverAllDiff)-(Target.ScaleHeight - OverAllDiff, 0), NewColor, BF
    'Top left to bottom right
    Case 34
    Target.Line (0, OverAllDiff * 2)-(OverAllDiff * 2, 0), NewColor
    'Fade to center from top right and bottom left
    Case 35
    Target.AutoRedraw = False
    Target.Line (0, Target.ScaleHeight - OverAllDiff)-(OverAllDiff, Target.ScaleHeight), NewColor
    Target.Line (Target.ScaleWidth - OverAllDiff, 0)-(Target.ScaleWidth, OverAllDiff), NewColor
    'Fade to center from top left and bottom right
    Case 36
    Target.Line (Target.ScaleWidth, Target.ScaleHeight - OverAllDiff)-(Target.ScaleWidth - OverAllDiff, Target.ScaleHeight), NewColor
    Target.Line (0, OverAllDiff)-(OverAllDiff, 0), NewColor
  'Wow I'm finally done!
  End Select
End Function
Function nolic(Target As Object)
Target.FontSize = 10
Target.ForeColor = vbBlack
Target.CurrentY = 0
Target.CurrentX = 2
Target.Print "Created with a SpiderTek Product"
Target.ForeColor = vbWhite
Target.CurrentY = 0
Target.CurrentX = 3
Target.Print "Created with a SpiderTek Product"
End Function
Private Sub Form_Click()
Static x As Integer
If x = 36 Then x = 0
x = x + 1
Gradeffect Me, x
Me.CurrentY = 200
Me.CurrentX = 3
Me.Print "You are at """ & x & """ of 36 total effects."
nolic Me
End Sub
Private Sub Form_Load()
FadeColors.Add vbBlack
FadeColors.Add vbRed
FadeColors.Add vbYellow
FadeColors.Add vbWhite
Gradeffect Me, 1
End Sub
Private Sub Form_Resize()
Gradeffect Me, 1
End Sub
```

