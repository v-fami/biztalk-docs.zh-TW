---
title: "轉換 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 788bf4a9-a63b-4fd3-93a2-6e34a1464049
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5abad7a5a7bae3c76fba58ecd92fc3384df5ca25
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-transformation-web-service"></a>轉換 Web 服務
轉換 Web 服務可讓外部應用程式提交至 ESB 應用程式的文件，並使用已部署的 Microsoft BizTalk 對應轉換。 不同於轉換代理程式時，此服務不會路由訊息到 BizTalk Messagebox 資料庫。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含此服務的兩個版本： ASP.NET (ASMX) 版本和 Windows Communication Foundation (WCF) 版本。 服務名稱就是**ESB。TransformServices**和**ESB。TransformServices.WCF**分別和服務會公開單一方法：  
  
-   **轉換。** 這個方法會採用做為參數**字串**，其中包含要轉換的訊息和**字串**，其中包含完整部署在 BizTalk 對應的名稱。 方法會傳回**字串**，其中包含已轉換的文件。 使用字串參數，可降低在異質環境; 中的互通性問題的風險不過，請記住，這是 Web 服務，因此您應該避免使用它來轉換 （Transformation Service，在 BizTalk 中較適合大型文件） 的大型文件。  
  
> [!NOTE]
>  根據預設，轉換 Web 服務不會設定為需要安全通訊端層 (SSL) 用戶端存取時。 您應該設定服務，讓需要 SSL 用戶端存取，並保護網際網路資訊服務 (IIS) Web 服務主機電腦與您使用網路層級 IPSec 和適當的檔案層級存取權的 BizTalk Server 之間的連線控制清單 (ACL) 權限。