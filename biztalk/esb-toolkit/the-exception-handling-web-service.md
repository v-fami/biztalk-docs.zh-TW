---
title: 例外狀況處理 Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dfe6ebdf-9b92-40c7-93fb-afd6c5f68aaa
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1bcc8146947f5e3cbaf58e31d1f515a055d102c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974303"
---
# <a name="the-exception-handling-web-service"></a>例外狀況處理 Web 服務
例外狀況處理 Web 服務接受的錯誤訊息，並將其發佈至 ESB 例外狀況入口網站。 用戶端應用程式可以建立例外狀況訊息，並將它們提交到 ESB，針對該例外狀況類型或泛型處理常式中，設定任何處理常式可以處理的例外狀況的地方。 這項服務的主要優點是它可讓參與 ESB 例外狀況處理機制的 ESB 應用程式外部的實體。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含這項服務的兩個版本： ASP.NET (ASMX) 版本和 Windows Communication Foundation (WCF) 版本。 服務名稱為**ESB。ExceptionHandlingServices**和**ESB。ExceptionHandlingServices.WCF**，分別與服務會公開單一方法：  
  
- **SubmitFault**。 這個方法會採用的執行個體**FaultMessage**類別，並沒有傳回值。  
  
  如需方法的例外狀況處理機制搭配運作的資訊，請參閱[使用 ESB 例外狀況管理](../esb-toolkit/using-esb-exception-management.md)。  
  
> [!NOTE]
>  根據預設，例外狀況處理 Web 服務未設定為需要 Secure Sockets Layer (SSL) 用戶端存取時。 您應該設定服務，因此它需要 SSL 用戶端存取和保護 Internet Information Services (IIS) Web 服務主機電腦和裝載的伺服器之間的連線**ESBExceptions**資料庫使用網路層級 IPSec 和適當的檔案層級存取控制清單 (ACL) 權限。