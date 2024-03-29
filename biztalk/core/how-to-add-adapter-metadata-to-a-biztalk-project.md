---
title: 如何將配接器中繼資料新增至 BizTalk 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e439e5bf-94b3-4582-bacc-b058e6eb8e17
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c95cfac206dad58e0093945d2495c7e725c849c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968801"
---
# <a name="how-to-add-adapter-metadata-to-a-biztalk-project"></a>如何將配接器中繼資料新增至 BizTalk 專案
「新增配接器中繼資料精靈」可讓您新增配接器中繼資料到 BizTalk 專案。 這項資料包含從協調流程與配接器通訊所需的配置、訊息類型以及連接埠類型。 對 應用程式配接器 (例如 FTP) 使用 「 新增配接器中繼資料精靈 」 ，可將這些應用程式配接器的對應結構描述提取至系統中 。 請注意，一般而言，HTTP 之類的傳輸配接器並不會使用結構描述。  
  
 下列程序帶您執行新增配接器中繼資料的一般步驟。  
  
### <a name="to-add-adapter-metadata-to-a-biztalk-project"></a>將配接器中繼資料新增至 BizTalk 專案  
  
1. 在您[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案的 [方案總管] 中以滑鼠右鍵按一下您的專案，按一下**新增**，然後按一下**加入產生的項目**。  
  
2. 在 **加入產生的項目- \<** <em>專案名稱</em>**\>** 對話方塊中，於**範本** 區段中，選取 **新增配接器**，然後按一下**開啟**。  
  
3. 在 [新增配接器中繼資料精靈] 中，在**選取配接器**頁面上，執行下列動作。  
  
   |使用|以進行此動作|  
   |--------------|----------------|  
   |配接器清單方塊|選取要新增至專案的已註冊配接器。|  
   |[SQL Server]|輸入 BizTalk 資料庫伺服器名稱。|  
   |[資料庫]|顯示所選取伺服器的「BizTalk 管理」資料庫清單。|  
   |通訊埠|選擇性。 顯示先前建立並儲存在「BizTalk 管理」資料庫中的連接埠清單。 只有設定為使用所選取配接器的連接埠才會顯示。|  
  
    按 [下一步] 。  
  
   > [!NOTE]
   >  嘗試加入產生的結構描述包含字元**System.XML.XMLConvert**類別不支援編譯錯誤的結果。  
  
4. 如果您使用靜態配接器，在**選取要匯入服務**頁面上，從樹狀檢視中，選取一組可用的服務，然後按一下**完成**。  
  
    – 或者 –  
  
    如果要使用動態的配接器，請遵循自訂使用者介面中的步驟來完成精靈。  
  
   在完成精靈之後，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 就會在方案總管中列出 .odx 和 .xsd 檔案。