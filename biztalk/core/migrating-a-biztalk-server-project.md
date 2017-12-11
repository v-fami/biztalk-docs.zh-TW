---
title: "移轉 BizTalk Server 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a4dde72-6555-4bf6-b90e-676aa65312ff
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2752203b0498a6cd5a4a8b6df6bc558c444e355
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="migrating-a-biztalk-server-project"></a>移轉 BizTalk Server 專案
[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]針對開發專案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以移轉至較新的環境，利用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]轉換。 如需支援的移轉版本，請參閱[支援升級路徑以及安裝指南](http://social.technet.microsoft.com/wiki/contents/articles/28554.biztalk-server-supported-upgrade-paths-and-installation-guides.aspx)。  
  
## <a name="biztalk-project-changes-after-running-the-conversion-wizard"></a>執行轉換精靈後 BizTalk 專案的變更  
 下表顯示如何[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]其中部分特定組態屬性重新放置在專案之後會轉換成較新和專案組態名稱變更，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。 大部分的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關的專案設定都位於**部署**專案設計工具 索引標籤。  
  
|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 專案|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案|  
|------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|  
|**內嵌追蹤資訊**輸出組態屬性|**定義 TRACE 常數**上建置選項**建置**專案設計工具 索引標籤|  
|**產生偵錯資訊**輸出組態屬性|**定義 DEBUG 常數**上建置選項**建置**專案設計工具 索引標籤|  
|**BPEL 規範**程式碼產生組態屬性|**BPEL 規範**程式碼專案的 [屬性] 視窗中的產生屬性|  
  
> [!NOTE]
>  BizTalk 專案現在有兩個組建類型：**發行**和**偵錯**，取代了**開發**和**部署**的前面版本。 不過，您將會繼續看見**開發**和**部署**從移轉的專案組態[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]。  
  
> [!CAUTION]
>  只有.btproj 和\*.btproj.user 專案檔選擇備份選項，在轉換期間會備份。 其他檔案必須手動備份。  
  
> [!CAUTION]
>  轉換期間將遺失對自動產生的項目 (例如 XSD 與 ODX 檔案) 所做的自訂設定。 對於將 Web 參考新增至 BizTalk 專案時產生的 XSD 檔案，結果也是一樣。  
  
## <a name="project-migration-and-delay-signing"></a>專案移轉與延遲簽章  
 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]專案使用[延遲簽章](http://go.microsoft.com/fwlink/p/?LinkId=140992)後可能會失敗建置程序期間正在轉換為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 這種情況**產生序列化組件**組建設定，移轉的專案組態不會設定為**關閉**。  
  
## <a name="project-migration-and-msmqt"></a>專案移轉與 MSMQT  
 MSMQT 不再是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的一部分。 如需有關如何這可能會影響專案移轉的詳細資訊，請參閱主題[MSMQT 過時](../core/msmqt-deprecation.md)。  
  
## <a name="project-conversion-requires-the-project-and-solution-file"></a>專案轉換需要專案與方案檔  
 如果您嘗試轉換 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 專案，但是卻沒有方案檔案，將會收到下列錯誤訊息：  
  
 **轉換專案檔時發生錯誤。子項目\<BIZTALK\>項目的\<VisualStudioProject\>不正確。**  
  
 專案轉換需要 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案中的方案檔 (.sln)。 如果方案檔不存在，您必須使用 [!INCLUDE[btsVStudioNet2005](../includes/btsvstudionet2005-md.md)] 建立一個，並將 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 專案新增到該方案。 然後執行 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 轉換精靈。  
  
> [!NOTE]
>  您可能會是轉換只專案檔 (.btproj) 使用 Visual Studio 專案。