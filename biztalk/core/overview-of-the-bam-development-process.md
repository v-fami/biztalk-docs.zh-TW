---
title: BAM 開發程序的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 098db3f6-2a61-4cc8-88c7-2299c2e2a55e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78ae5f1c61f2a00359e88acd75c093e2b6c2fb91
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25972500"
---
# <a name="overview-of-the-bam-development-process"></a>BAM 開發程序概觀
本主題描述開發程序和用來存放 BAM 資料的資料庫與資料表。  
  
## <a name="prerequisites-for-developing-with-bam"></a>開發 BAM 的必要條件  
 開始開發 BAM 之前，請注意下列必要條件：  
  
-   為了檢測應用程式，您必須已經部署活動。  
  
-   您必須具有 SQL Server 資料庫的 DBO 權限，並且是「BAM 事件寫入器角色」資訊安全內容的成員。  
  
-   您必須使用 Microsoft .NET 4 來開發應用程式。 雖然建議使用 C#，您還是可以使用任何 .NET 語言。  
  
-   您必須在電腦上安裝 Microsoft.BizTalk.BAM.EventObservation.dll。 您可以使用兩種方法來取得 DLL。  
  
    -   使用 BizTalk Server 組態管理員來安裝 BAM 工具。 建議您使用「組態管理員」，是因為它會置入有助於升級的適當登錄。 如需有關如何設定 BAM 的詳細資訊，請參閱[使用組態管理員設定 BAM 工具](http://go.microsoft.com/fwlink/?LinkId=70561)(http://go.microsoft.com/fwlink/?LinkId=70561)。  
  
    -   從已經安裝這些 DLL 的電腦中複製它們。 DLL 位於 Microsoft BizTalk Server\<版本\>\Tracking 資料夾。  
  
## <a name="bam-development-process"></a>BAM 開發程序  
 下圖描述 BAM 開發流程。  
  
 ![BAM 開發工作流程](../core/media/dwb-bamdevelopmentflowc.gif "dwb_bamdevelopmentflowc")  
  
 下列程序列出開發 BAM 解決方案的基本步驟。  
  
#### <a name="to-develop-a-bam-enabled-solution"></a>開發啟用 BAM 功能的解決方案  
  
1.  使用 Excel 的 BAM 增益集建立 BAM 觀察模型。  
  
    > [!NOTE]
    >  可以在 BAM API （BizTalk Server 範例） 中找到此程序中所述的步驟的範例[ http://go.microsoft.com/fwlink/?LinkId=69968 ](http://go.microsoft.com/fwlink/?LinkId=69968)。  
  
2.  使用 BAM 管理公用程式，將活動部署至 PID。  
  
3.  加入 BAM EventStream 程式碼以檢測應用程式。  
  
4.  執行應用程式。 當您這麼做時，程式碼將會：  
  
    -   新增預留位置記錄至 BAM_<\<*活動名稱*\>_Active 資料表。  
  
    -   更新記錄中的資料項目。  
  
    -   結束活動並將記錄移到 BAM_\<* 活動名稱 * *\>_completed 資料表。  
  
## <a name="where-bam-data-is-stored"></a>儲存 BAM 資料的位置  
 BAM 提供 EventObservation 命名空間，其中包含可用來處理 BAM 事件的 EventStream 類別。  
  
 BAM 追蹤資料會儲存在 BAM 主要匯入資料庫 (PID) 中。 當您使用 BAM 管理公用程式部署觀察模型時，會在 PID 中建立下列五個資料表。  
  
|名稱|Description|  
|----------|-----------------|  
|作用中資料表|名為 bam_<\<*活動名稱*\>（_a），此資料表會保存此類型的活動尚未完成的。|  
|作用中關係資料表|名為 bam_<\<*活動名稱*\>_ActiveRelationships，此資料表包含活動的相關的活動尚未完成。|  
|接續資料表|名為 bam_<\<*活動名稱*\>_continuations，此資料表列出活動之活動的接續。|  
|完成的資料表|名為 bam_<\<*活動名稱*\>_completed。|  
|完成的關係資料表|名為 bam_<\<*活動名稱*\>_CompletedRelationships，此資料表包含活動的已完成相關的活動。|  
  
 您可以在 BAM 活動中擷取四種類型的資料：  
  
-   字串  
  
-   日期/時間 (一般稱為里程碑)  
  
-   Integer  
  
-   Float