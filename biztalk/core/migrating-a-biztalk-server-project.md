---
title: 移轉 BizTalk Server 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a4dde72-6555-4bf6-b90e-676aa65312ff
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0fd15de7aec81c046ab6b2fc23b6c63a1ec0615
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752702"
---
# <a name="migrating-a-biztalk-server-project"></a>移轉 BizTalk Server 專案
[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 針對開發專案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以移轉至較新的環境，使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]轉換。 如需支援的移轉版本的清單，請參閱 <<c0> [ 支援的升級路徑與安裝指南](http://social.technet.microsoft.com/wiki/contents/articles/28554.biztalk-server-supported-upgrade-paths-and-installation-guides.aspx)。  

## <a name="biztalk-project-changes-after-running-the-conversion-wizard"></a>執行轉換精靈後 BizTalk 專案的變更  
 下表顯示如何[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]專案組態名稱變更，和其中部分特定組態屬性，將專案重新配置所轉換至較新[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。 大部分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關的專案設定都位於**部署**] 索引標籤的 [專案設計工具。  


| [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 專案 | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案 |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|             **內嵌追蹤資訊**輸出組態屬性             |      **定義 TRACE 常數**建置選項**建置**] 索引標籤的 [專案設計工具       |
|           **產生偵錯資訊**輸出組態屬性           |      **定義 DEBUG 常數**建置選項**建置**] 索引標籤的 [專案設計工具       |
|              **BPEL 合規性**程式碼產生組態屬性              |       **BPEL 合規性**程式碼專案的 [屬性] 視窗中的產生屬性        |

> [!NOTE]
>  BizTalk 專案現在有兩種組建類型：**發行**並**偵錯**，取代了**開發**並**部署**的稍早版本。 不過，您將會繼續看見**Development**並**部署**從移轉的專案組態[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]。  
> 
> [!CAUTION]
>  只有\*.btproj 和\*。 因為選擇備份選項，在轉換期間備份.btproj.user 專案檔。 其他檔案必須手動備份。  
> 
> [!CAUTION]
>  轉換期間將遺失對自動產生的項目 (例如 XSD 與 ODX 檔案) 所做的自訂設定。 對於將 Web 參考新增至 BizTalk 專案時產生的 XSD 檔案，結果也是一樣。  

## <a name="project-migration-and-delay-signing"></a>專案移轉與延遲簽章  
 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 專案使用[延遲簽章](http://go.microsoft.com/fwlink/p/?LinkId=140992)可能無法建置程序期間進行的轉換後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如果此情形**產生序列化組件**組建設定已移轉的專案組態不會設定為**關閉**。  

## <a name="project-migration-and-msmqt"></a>專案移轉與 MSMQT  
 MSMQT 不再是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的一部分。 如需這如何影響專案移轉的詳細資訊，請參閱主題[MSMQT 過時](../core/msmqt-deprecation.md)。  

## <a name="project-conversion-requires-the-project-and-solution-file"></a>專案轉換需要專案與方案檔  
 如果您嘗試轉換 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 專案，但是卻沒有方案檔案，將會收到下列錯誤訊息：  

 **轉換專案檔時發生錯誤。子項目\<BIZTALK\>項目的\<VisualStudioProject\>無效。**  

 專案轉換需要 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案中的方案檔 (.sln)。 如果方案檔不存在，您必須使用 [!INCLUDE[btsVStudioNet2005](../includes/btsvstudionet2005-md.md)] 建立一個，並將 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 專案新增到該方案。 然後執行 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 轉換精靈。  

> [!NOTE]
>  您可以將轉換只有專案檔 (.btproj) 使用 Visual Studio 專案。