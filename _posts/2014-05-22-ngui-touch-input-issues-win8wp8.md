---
layout: post
title: NGUI Touch Input Issues (WP8/Win8)
author: Michael Quandt
---
NGUI is widely used, and upgrading from older versions can be challenging depending on the complexity of your game. I have seen this issue pop up a few times while converting projects and thought I might note it down with a quick solution.

When converting to the Windows Store or Windows Phone you might encounter an issue where a button seems to do nothing when tapped. This occurs because the OnClick event is actually firing twice, in quick succession, often cancelling out the effect of the original press.

To resolve this you just need to add a small delay check to ensure it doesn't fire twice. (This is known as *debouncing* in electronics)

```csharp
    private float _prevPress;
    void OnClick()
    {  
        if (Time.realtimeSinceStartup < (_prevPress + 0.15f))
            return;
        else
            _prevPress = Time.realtimeSinceStartup;
        
        // Handle the click here
    }
```
You can add this to the button with the problem, or integrate this into UIButton in NGUI to cover all buttons.
