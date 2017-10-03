---
title: "建立 Web 服務與 Web 方法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, publishing
- Web services, schemas
- orchestrations, naming conventions
- Web services, naming conventions
- schemas, Web services
ms.assetid: a7c47000-501c-47b1-bafa-82370585c1db
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74065489e427ae0612897f1f333e3c8e154a535f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-web-services-and-web-methods"></a>建立 Web 服務與 Web 方法
將結構描述發佈為 Web 服務時，您會在 [BizTalk Web 服務發佈精靈] 中控制 Web 服務與 Web 方法的建立。 您可以在 Web 服務頁面上可用的樹狀結構中，將 Web 服務描述、Web 服務和 Web 方法重新命名。 您可以新增和移除 Web 服務與 Web 方法。 精靈會使用所選要求結構描述的根項目名稱，當作輸入參數名稱。 Web 方法的傳回值會傳回回應結構描述。  
  
> [!NOTE]
>  ASP.NET Web 用戶端可能會合併相同型別的 in 和 out 參數，以變更 Web 方法簽章。 例如，ASP.NET Web 用戶端可能會變更 BizTalk Web 方法，從**string myService （字串一部分）**至**void myService （ref 字串的一部分）**。  
  
> [!NOTE]
>  如果您收到定義為單向連接埠、 Web 方法回應型別是**void**和 Web 用戶端傳回任何資訊。 SOAP 配接器和協調流程，不會將所擲回的例外狀況傳回 Web 用戶端。  
  
## <a name="web-services-naming-conventions-for-published-orchestrations"></a>已發佈協調流程的 Web 服務命名慣例  
 [BizTalk Web 服務發佈精靈] 會根據您在 [Web 服務] 頁面中所定義的 Web 服務描述，產生 Web 服務 (.asmx) 檔案名稱。 下列資料表會顯示 Web 服務檔案名稱的預設值。  
  
|產生的 Web 服務|檔案名稱|  
|---------------------------|---------------|  
|BizTalkWebService|Visual Studio Web 服務專案名稱|  
|WebService1|Web 服務 (.asmx) 檔案名稱|  
|WebMethod1|Web 方法名稱|  
  
 所產生的 Web 服務不會反映剩餘節點的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [結構描述發佈為 Web 服務](../core/publishing-schemas-as-a-web-service.md)   
 [如何使用 BizTalk Web 服務發佈精靈將結構描述發佈為 Web 服務](../core/publish-schemas-as-web-services-with-biztalk-web-services-publishing-wizard.md)