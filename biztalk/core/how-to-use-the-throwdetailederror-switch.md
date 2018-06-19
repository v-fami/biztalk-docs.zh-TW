---
title: 如何使用 ThrowDetailedError 參數 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web services, security
- Web services, debugging
ms.assetid: 8a8af3c0-a9a2-42fe-b0be-a5a106403747
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90929015e2d1d0567af0ccc5c51c6aae450d49c8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970316"
---
# <a name="how-to-use-the-throwdetailederror-switch"></a>如何使用 ThrowDetailedError 參數
如果發生錯誤時，Web 用戶端會接收泛型**SoapException**。  
  
 若要偵錯已發佈的 Web 服務，您可以在 Web.config 檔案中加入某個參數，以便控制從該發佈的 Web 服務傳回之例外狀況詳細資料的等級。  
  
 Web.config 檔案包含應用程式設定參數**ThrowDetailedError**。 **False**是預設設定**ThrowDetailedError**。 如果您將設定變更為**True**，伺服器 proxy 將內部例外狀況資訊傳回給 Web 用戶端，讓您偵錯已發佈的 Web 服務。  
  
 下列 XML 程式碼示範**ThrowDetailedError**下的 Web.config 檔案中出現的交換器\<appSettings\>節點：  
  
```  
<appSettings>  
  <add key="ThrowDetailedError" value="False" />  
<appSettings/>  
```  
  
> [!IMPORTANT]
>  依照預設，BizTalk Server 不會將內部例外狀況資訊傳回給 Web 用戶端，因為這種資訊可能包含機密資訊 (例如應用程式呼叫堆疊)。 偵錯之後，您應該設定**ThrowDetailedError**設**False**。  
  
## <a name="see-also"></a>請參閱  
 [偵錯已發佈的 Web 服務](../core/debugging-published-web-services.md)