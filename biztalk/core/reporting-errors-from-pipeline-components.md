---
title: 報告管線元件錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IErrorInfo object
- pipeline components [custom], errors
- SetErrorInfo method
- Exception object
ms.assetid: ad7c519e-829a-4a92-a42f-3e367d5dbaa8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a979b894715055b979ecae8c66ecb3fa19ba603
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018120"
---
# <a name="reporting-errors-from-pipeline-components"></a>報告管線元件錯誤
管線元件會使用兩種方法來報告錯誤：  
  
-   如果是 .NET 元件，則會擲回例外狀況。  
  
-   對於以 COM 為基礎的元件，藉由設定**ErrorInfo**物件並傳回失敗 HRESULT。  
  
## <a name="reporting-errors-from-net-pipeline-components"></a>報告 .NET 管線元件錯誤  
 若要報告錯誤，.NET 管線元件需要擲回例外狀況，以報告此錯誤的描述。 若要報告擲回錯誤之元件的名稱，請設定**來源**屬性**例外狀況**物件。  
  
 傳訊引擎會使用**訊息**並**來源**的屬性**例外狀況**来報告錯誤的物件。 下列訊息會寫入事件記錄：  
  
 "時發生失敗執行 [接收&#124;傳送] 管線：\<管線名稱\>來源：\<來源\>[接收位置&#124;傳送埠:]\<位置&#124;的連接埠名稱\>原因：\<訊息\>。 」  
  
## <a name="reporting-errors-from-com-pipeline-components"></a>報告 COM 管線元件錯誤  
 為了報告錯誤，COM 管線元件會執行下列動作：  
  
1. 管線元件集**IErrorInfo**藉由呼叫物件**SetErrorInfo**方法。  
  
2. 管線元件會將失敗的 HRESULT 傳給傳訊引擎。  
  
   傳訊引擎會使用**Ierrorinfo**並**GetDescription**的屬性**IErrorInfo**来報告錯誤的物件。 如果未設定來源，則會使用此元件的名稱。 如果描述不是集合或整個**ErrorInfo**未設定物件，傳回的 HRESULT 會報告而不是描述。 下列訊息會寫入事件記錄：  
  
   "無法執行 [接收&#124;傳送] 管線：\<管線名稱\>來源： \<Ierrorinfo\> [接收位置&#124;傳送埠:]\<位置&#124;連接埠名稱\>原因： \<GetDescription 或 HRESULT\>。 」  
  
## <a name="see-also"></a>另請參閱  
 [開發自訂管線元件](../core/developing-custom-pipeline-components.md)