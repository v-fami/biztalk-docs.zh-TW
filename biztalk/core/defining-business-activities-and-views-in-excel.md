---
title: 在 Excel 中定義商務活動和檢視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], creating business activities
- monitoring business activities [BAM], creating business activities
ms.assetid: 000532f0-cb9a-40ac-a6c5-a8bd4e49f8d0
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91b9d3b213a6a6429759c0bb0d826798afa36da3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239678"
---
# <a name="defining-business-activities-and-views-in-excel"></a>在 Excel 中定義商務活動和檢視
建立任何 BAM 解決方案時的第一個步驟是，找出您有興趣的資料，並釐清解譯此項資料所應採用的方式。 若要這樣做，您可以使用 Excel 的 BAM 增益集。 此增益集可讓您藉由定義商務活動來定義您希望的「感興趣資料」清單。 您也可以定義解譯資料以及向不同類別的商務使用者顯示資料的方式。  
  
 此 BAM 增益集還可以用來定義彙總。  
  
 您也可以重新命名活動項目；例如，某些使用者熟悉的詞彙可能不符合活動中對應資料項目的名稱。 因此，如果檢視使用不同的語言，便可以構成重新命名的理由。  
  
 完成活動定義之後，Excel 會產生隨機的預覽資料，以便您用來定義需要的圖表和其他的簡報方法。 如需預覽資料的詳細資訊，請參閱[如何使用樞紐分析表](../core/how-to-use-the-pivottable.md)。  
  
 完成的活動定義會定義執行商務程序時必須收集的資料點和事件。 您可以從各種來源取得該 BAM 增益集。  
  
 您可以安裝 BAM 增益集 XLA 期間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。 如需詳細資訊，請參閱[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)  
  
 BAM。XLA 檔案會安裝在下列位置：  
  
-   如果在電腦上沒有安裝 Microsoft Office，則 BAM.xla 會安裝至 files\microsoft BizTalk Server 20*xx*\ExcelDir\ 資料夾。  
  
-   如果已安裝 Microsoft Office，則 BAM.xla 會安裝 \Program Files\Microsoft Office\OFFICE*xx*\Library\ 資料夾。  
  
 您也可以將 BAM.xla 從另一台電腦上的共用資料夾複製至您的電腦。 然後從 XLA 複製到的位置加以選取，以註冊 XLA。  
  
 若要啟用 BAM 增益集在 Excel 功能表工具列上，按一下**檔案**功能表，然後按一下 **選項**，然後按一下 **增益集**。選取**商務活動監控**，然後按一下 **移**，在 Ad 單元視窗中，選取核取方塊旁的 **商務活動監控**，然後按一下  **確定**。  
  
> [!NOTE]
>  使用 BAM 增益集可以避免 Excel 在兩個執行個體載入至相同處理程序的情況下執行。  使用增益集時，相同處理程序中出現多個執行個體的情形可能會在下列狀況中發生：  
>   
>  開啟 Excel 試算表並啟用 BAM 增益集後，再按兩下其他的 Excel 試算表時，Excel 會嘗試將試算表載入目前執行中的執行個體。  
>   
>  開啟 Excel 試算表並啟用 BAM 增益集後，再使用 [檔案/開啟舊檔] 功能表選項載入另一份 Excel 試算表。  
  
 在這種情況下，您就無法正確使用增益集。 若要在 BAM 增益集啟用時開啟多份 Excel 試算表，您必須另外開啟新的 Excel 複本，然後再將試算表載入至這個 Excel 執行個體。  
  
> [!NOTE]
>  當您在 Excel 中使用 BAM.xla 時，您可能會收到錯誤 「 此活頁簿已經遺失其 VBA 專案、 ActiveX 控制項和其他相關的可程式性的功能 」。 如需有關錯誤的詳細資訊，請參閱[疑難排解 BAM](../core/troubleshooting-bam.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何定義商務活動](../core/how-to-define-a-business-activity.md)  
  
-   [定義 BAM 檢視](../core/defining-a-bam-view.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用 BAM 監控商務活動](../core/monitoring-business-activities-with-bam.md)