---
title: "建立 BizTalk 專案時的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, size
- map type name
- projects, naming conventions
- projects, planning
ms.assetid: f6c3dc71-105f-46af-9e6e-9a4c3b982d8c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0302d2329f848352f55d15f0c6e21bbdf72b0ca
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="considerations-when-creating-biztalk-projects"></a>建立 BizTalk 專案時的考量
本節提供使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立 BizTalk 專案時應考量的資訊。  
  
## <a name="avoid-compilation-errors-caused-by-projects-that-are-too-large"></a>避免專案太大所造成的編譯錯誤  
 若專案產生一個大於 75MB 的組件，則 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 編譯器無法成功編譯專案。 當編譯器到達大小限制，它就會發出嚴重錯誤 CS0013 「 中繼資料寫入檔案非預期的錯誤\<filename\>「 暫止。  
  
 若要避免此問題，建議您，除非絕對必要，否則專案不要超過 10MB。 為什麼？  
  
-   較小的專案比較容易部署，因為其中的部署步驟較少。 專案愈小，其步驟更有可能緊密相關 -- 管理交易夥伴折扣或處理 RFP。  
  
-   使用較小的專案比較容易隔離錯誤、部署問題以及其他問題。 在具有 140 個結構描述與許多自訂對應及指令碼的專案中尋找錯誤，比在只具有 10 個結構描述與少數自訂對應及指令碼的專案中尋找錯誤更為困難。  
  
-   將大型專案分隔成較小的專案可降低複雜性。 較小的專案較易於管理。  
  
-   較小的專案編譯較快速。  
  
-   將具有許多不相關結構描述的大型專案分割成具有強烈相關結構描述的較小型專案可產生更好的效能。 這是因為每次僅載入其中一些組件。  
  
## <a name="avoid-using-the-project-name-as-the-map-type-name"></a>避免使用專案名稱作為對應類型名稱  
 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 新增對應到 BizTalk 專案時，請勿使用專案名稱做為類型名稱。 如果您這樣做，編譯器會產生類似的一或多個錯誤 」 的型別名稱\<名稱\>' 不存在於型別 」。  
  
 若要在 BizTalk 專案中變更對應的類型名稱，按一下 [方案總管] 窗格中的對應，然後在 [屬性] 窗格中查驗類型名稱屬性。 若是相同，則需要加以修改，確定變更所有依賴它的組態。  
  
## <a name="visual-studio-team-system-support"></a>Visual Studio Team System 支援  
 中的 BizTalk 專案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]不是直接執行支援的所有功能[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]Team System。 原始檔控制功能[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]Team System 支援 BizTalk Server。 Visual SourceSafe 亦完全支援 BizTalk 專案成品的追蹤和版本管理。