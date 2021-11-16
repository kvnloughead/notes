---  
Title: errors  
Category: default  
Author: Kevin Loughead  
Date: 2021-11-15  
Tags:   
---  

## 'dangerouslySetInnerHTML doesn't match'
- See [this thread](https://stackoverflow.com/questions/64079321/react-tooltip-and-next-js-ssr-issue). 
- Solution: don't use `dangerouslySetInnerHTML` until component is mounted

```jsx
import React, { useEffect, useState } from 'react';

const [isMounted,setIsMounted] = useState(false); 
useEffect(() => {
  setIsMounted(true);
},[]);
 
return (<div>
      {isMounted && <ReactTooltip id={"mytip"} effect={"solid"} />}

      <span data-tip={"Tip Here"} data-for={"mytip"}>Hover me</span>
</div>)
```