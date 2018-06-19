---
title: 實作搜尋方法的 Managed 資料流管線元件中 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline interfaces, IStream interface
- pipeline components [custom], code samples
- IStream interface
- Seek method
ms.assetid: 2e546c41-822d-4e22-a8f6-8959072ef3d2
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5181957f691502dcc2b09a367c31de575097d1a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256518"
---
# <a name="implementing-a-seek-method-in-a-managed-streaming-pipeline-component"></a><span data-ttu-id="0b302-102">實作搜尋方法的 Managed 資料流管線元件中</span><span class="sxs-lookup"><span data-stu-id="0b302-102">Implementing a Seek Method in a Managed Streaming Pipeline Component</span></span>
<span data-ttu-id="0b302-103">原生**IStream**介面不會提供方法來檢查目前的資料流位置，因此傳訊引擎會使用下列**搜尋**方法。</span><span class="sxs-lookup"><span data-stu-id="0b302-103">The native **IStream** interface does not provide a method to check the current stream position, so the messaging engine uses the following **Seek** method.</span></span>  
  
```  
pStream->Seek(0, STREAM_SEEK_CUR, &pNewPosition);  
```  
  
 <span data-ttu-id="0b302-104">這個方法不會移動資料流指標，而是會查詢目前的位置。</span><span class="sxs-lookup"><span data-stu-id="0b302-104">This method does not move the stream pointer; instead it queries the current position.</span></span> <span data-ttu-id="0b302-105">因此如果您實作搭配不可搜尋資料流的管線元件，您可以使用**Stream.Seek**方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0b302-105">So if you implement a pipeline component that works with a nonseekable stream, you can use the **Stream.Seek** method as in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b302-106">範例</span><span class="sxs-lookup"><span data-stu-id="0b302-106">Example</span></span>  
  
```csharp  
override public long Seek(long offset, SeekOrigin origin)  
{  
   long pos = -1;  
  
   switch(origin)  
   {  
      case SeekOrigin.Begin :  
         pos = offset;  
         break;  
      case SeekOrigin.Current :  
         pos = Position + offset;  
         break;  
      case SeekOrigin.End :  
         break;  
   }  
  
   // We generally disallow seeking of the stream  
   // However, in unmanaged code, many people use Seek(0,CURR) to retrieve    // the current position  
   // Special case (that is, if Seek does not change position, do not   
   // throw an exception)  
   if (pos==Position)  
   {  
      return pos;  
   }  
   else  
   {  
      throw new NotSupportedException("ForwardOnlyEventingReadStream does not support Seek()");  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b302-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b302-107">See Also</span></span>  
 [<span data-ttu-id="0b302-108">開發自訂管線元件</span><span class="sxs-lookup"><span data-stu-id="0b302-108">Developing Custom Pipeline Components</span></span>](../core/developing-custom-pipeline-components.md)