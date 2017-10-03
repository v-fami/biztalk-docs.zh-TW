---
title: "配接器元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 383e8bcb-2b4d-40f9-9e98-f49e8d6f30f7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2a5f2a78a9ea555d22f585c0aa50eda65b6c287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-components"></a>配接器元件
自訂配接器共用由原生配接器所使用的標準化組態、管理和設定機制。 運用配接器架構的標準化，自訂配接器的管理藉由使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 進行。  
  
 下圖顯示自訂配接器的主要元件： 配接器登錄檔、 配接器設計階段元件，以及配接器執行階段元件。  
  
 ![](../core/media/elementsofanadapter.gif "ElementsOfAnAdapter")  
  
## <a name="adapter-registry-file"></a>配接器登錄檔  
 配接器的特定資訊必須在登錄和 BizTalk 管理資料庫中註冊。 配接器的別名、接收處理常式、接收位置和傳輸類型一類的資訊，都稱為中繼資料。 這些中繼資料項目，都是在使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 手動進行配接器註冊期間所建立的。 或者，您可以執行 [配接器登錄精靈] (AdapterRegistryWizard.exe) SDK 公用程式為自訂配接器產生登錄檔。 按兩下這個登錄檔，或按一下**匯入**上**檔案**功能表使用登錄編輯程式 (regedit32.exe) 會將中繼資料寫入登錄。  
  
> [!NOTE]
>  執行此登錄檔並不會將配接器資訊新增至 BizTalk 管理資料庫。 您必須使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台]，以手動方式進行。  
  
## <a name="design-time-component"></a>設計階段元件  
 自訂配接器的使用者介面 (UI) 是使用配接器架構實作的。 這對 UI 開發是具有生產力的方法，因為 UI 是從提供做為配接器組件一部分的 XML 結構描述轉譯的。 您需要小量的程式碼，才能將結構描述的內容轉換成 UI 以設定配接器的屬性。  
  
 如需讓協調流程與應用程式配接器通訊 (例如 SQL 配接器)，[新增配接器中繼資料精靈] 可讓您將配接器中繼資料，例如結構描述、訊息類型及連接埠類型，新增到 BizTalk 專案。 搭配應用程式配接器使用 [新增配接器中繼資料精靈]，即可將對應的結構描述提取至系統中。 要叫用這個精靈從 BizTalk （非配接器） 專案中的，以滑鼠右鍵按一下專案，指向**新增產生的項目**，按一下 **新增配接器中繼資料**然後從清單中選取登錄若要匯入配接器中繼資料的介面卡。  
  
## <a name="run-time-component"></a>執行階段元件  
 配接器通常兩個公用的執行階段元件所組成： 實作訊息接收者和實作訊息傳送者元件的元件。 這些元件可能會在相同的組件中部署，或是在兩個不同的組件中部署。  
  
#### <a name="receive-adapter"></a>接收配接器  
 接收配接器負責將網路/資料來源資料流附加到訊息內文，以建立新的 BizTalk 訊息。 它也會新增與接收資料的端點有關的任何中繼資料，然後將該訊息提交至傳訊引擎。 配接器會將接收端點的資料刪除，或是將適當的認可訊息傳送到用戶端，以表示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 已接受資料。  
  
#### <a name="send-adapter"></a>傳送配接器  
 傳送配接器負責使用其特定的傳輸通訊協定，將 BizTalk 訊息傳送到指定的端點。  
  
## <a name="see-also"></a>另請參閱  
 [什麼是配接器架構？](../core/what-is-the-adapter-framework.md)