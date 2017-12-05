---
title: "BizTalk Server 中的組件的部署方式 |Microsoft 文件"
description: "組件部署至 GAC 中，並啟用 BizTalk Server 中的組件的版本控制"
ms.custom: 
ms.date: 01/21/2016
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f99ed5-b64a-4a38-99d7-83070fb69030
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb6c787219855ca219808fc1e95c0caefbf12a9d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="biztalk-assemblies"></a>BizTalk 組件
Microsoft BizTalk Server 與 .NET Framework 最重要的部分是所有的 BizTalk Server 成品、對應、結構描述、協調流程以及管線都會編譯為 .NET 組件。 此設計的兩個最重要含意是這些組件必須具有強式名稱，因此它們也遵循 .NET 版本管理規則。 其主要含意為，一旦針對另一個 .NET 專案或組件 (包括 BizTalk 專案) 的特定版本建置 BizTalk 專案，該專案會繼續使用此版本，直到再針對較新的版本重新建置它為止。  
  
## <a name="net-versioning-and-assemblies"></a>.NET 版本管理與組件  
 在開發期間發生的一個與 .NET 版本管理相關之常見問題是，BizTalk 專案上的版本號碼未變更，而且在重新部署組件時，未停止後啟動載入類型的 BizTalk 主控件執行個體。  
  
 當再次執行程序時，變更不會生效。 這是由於將 .NET 組件載入記憶體的方式所造成。 因為主控件已經具有組件的記憶體中複本，所以將新複本放入「全域組件快取」時，不會重新載入組件。 例如，若已部署和執行搭配協調流程之 1.0.0.0 版的組件，而協調流程已變更，但是版本號碼未變更，則變更不會生效。 在主控件執行個體停止後，會釋放組件的記憶體中複本，當主控件執行個體再次啟動時，它會重新載入組件的新複本並取得變更。 若已部署新版本，例如 2.0.0.0 版，就會將它載入，然後變更也會生效。  
  
 部署組件到 BizTalk Server 是一個包含兩部分的程序。 第一個部分是傳統的 .NET 組件部署，在此會將強式名稱的組件部署到使用組件的每個伺服器上的「全域組件快取」(GAC)。 第二步是將組件的中繼資料及其類型部署到 BizTalk Server 管理資料庫。 當 BizTalk Server 載入 BizTalk Server 組件時，最常使用其強式名稱來載入它們，您可以在管理資料庫中找到這些名稱。  
  
## <a name="deploying-biztalk-server-assemblies-to-the-gac"></a>將 BizTalk Server 組件部署到 GAC  
 開發人員建立的 BizTalk Server 成品會編譯為衍生自內建 BizTalk Server 類型的類別。 例如，協調流程會變成衍生自 Microsoft.BizTalkXLANGs.BTXEngine.BTXService 類別的類別。 這是因為組件中的這些基底類別已部署到「全域組件快取」，而這些組件對 GAC 中的其他組件有相依性，所以開發人員的組件也必須部署到 GAC。  
  
 部署到「全域組件快取」的 BizTalk Server 成品也因此必須使用強式名稱的另一個重要含意是，強式名稱的組件不能呼叫其他不是強式名稱的組件。 這表示由開發人員建立以供這些 BizTalk 組件使用的任何組件，也必須使用強式名稱。 同樣的，部署到 GAC 的組件若未使用特定路徑載入其他組件，則必須從 GAC 載入這些組件。  
  
 會將管線元件新增至 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的開發人員工具箱，讓它們可供拖曳至管線設計師上。 將 BizTalk Server 管線編譯為 .NET 組件時，會將管線各個階段中所有元件的資訊編譯為組件。 此管線部署到 BizTalk Server 時, 的元件，包括其檔案名稱資訊插入 BizTalk 管理資料庫和管線組件部署到 GAC。 BizTalk 管線元件相依於任何其他組件也必須部署到 GAC 以便在執行階段找到。 管線元件組件也必須複製到可存取 BizTalk Server\Pipeline 元件目錄中，但會由 BizTalk 管線在執行階段。 管線執行時會載入這些元件，並適時呼叫它們所實作的介面。  
  
## <a name="see-also"></a>請參閱  
 [執行階段架構](../core/runtime-architecture.md)