---
title: 使用訂單處理常式物件與後端系統通訊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IOrderHandler interface
- process management solution tutorial, IOrderHandler interface
ms.assetid: b9fe4120-bf2a-4d15-a34b-6b98f026b984
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d7621c4e5737def0e9fc0682de709ae57f98790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288062"
---
# <a name="using-the-order-handler-object-to-communicate-with-backend-systems"></a>使用訂單處理常式物件與後端系統通訊
商務程序管理解決方案和傳統的後端訂單系統有多種通訊方式，而後端訂單系統就是接收最後訂單的網路供給系統。 解決方案會使用 Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 中的 .NET 遠端處理功能來和供給系統通訊。  
  
 解決方案使用一般的技術，藉由使用介面定義後端系統的存取物件。 將介面放置在個別的組件中，用戶端組件就可以存取遠端物件，而不需要存取編譯的組件。  
  
 **IOrderHandler**介面會定義與後端訂單系統通訊的方法。 介面包含了分析、啟動、取消以及完成訂單的方法。 介面也提供了識別服務類型的方法，這是在取消訂單時必須使用的方法。  
  
 **CableOrder1**， **CableOrder2**，和附屬協調流程會使用**OrderHandlerWrapper**實作物件**IOrderHandler**. **OrderHandlerWrapper**物件，接著，會叫用的遠端執行個體**OrderHandler**所提供物件**CableProvisioningSystemServer**可執行檔。 使用包裝函式物件不僅符合使用 .NET 遠端處理來與後端訂單系統通訊的商務需求，同時也會啟用例外狀況處理元件的重試功能。  
  
 因為其中一個必須能序列化在協調流程中參考的每個物件**OrderHandlerWrapper**也可以序列化。 使用**OrderHandlerWrapper**隔離協調流程的序列化程式碼。  
  
 如果您查看程式碼時，您將 se， **OrderHandlerWrapper**物件會明確實作**ISerializable**介面。 物件必須處理自己的序列化，因為物件使用的非預設的建構函式。  
  
 使用 .NET 遠端處理來與後端系統通訊比使用傳訊更有效率。 另外，.NET 遠端處理會將協調流程更緊密地繫結到後端系統，而這是單純的傳訊解決方案無法做到的。 使用 .NET 遠端處理也可避免解決方案利用內建的 BizTalk Server 功能來重試要求。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [程序管理員邏輯](../core/process-manager-logic.md)