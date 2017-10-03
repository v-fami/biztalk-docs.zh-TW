---
title: "如何定義商務活動 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business activities, creating [Excel add-in]
- monitoring business activities [BAM], creating business activities [Excel add-in]
- monitoring business activities [BAM], Excel add-in
ms.assetid: 305e3718-46b4-45df-bd52-f7ae36621576
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74cb0bb6f2bd0a5f92f6029dda65d55d219bcc12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-define-a-business-activity"></a>如何定義商務活動
若要指示您必須為報告收集的資料，則必須定義 BAM 活動。 這個定義包含您想要 BAM 追蹤的重要里程碑及資料項目的清單。請使用 BAM Excel 增益集來建立活動，如下列程序所示。  
  
> [!NOTE]
>  一旦部署活動之後，可在活動上採取的動作便會受到限制。 特別是，您不可以從活動刪除項目，除非您準備請系統管理員解除部署整個 BAM 活動和檢視集，然後再重新部署。 這樣可能會造成暫時看不見資料或資料遺失，除非系統管理員執行資料備份與還原。  
  
### <a name="to-create-a-business-activity"></a>建立商務活動  
  
1.  開啟 Microsoft Excel。  
  
2.  在功能表的工具列上，按一下**BAM**功能表項目，然後按一下**BAM 活動**。  
  
     **商務活動監控活動精靈**隨即出現。  
  
3.  按一下**新活動**。  
  
     **新活動** 對話方塊隨即出現。  
  
4.  輸入之活動的描述性名稱**活動名稱**文字方塊。  
  
> [!NOTE]
>  活動必須包含至少一個活動項目。  
  
#### <a name="to-create-a-new-item"></a>建立新項目  
  
1.  按一下**新項目**。  
  
2.  在**新增活動項目**對話方塊中，於**新增活動項目**方塊中，輸入活動項目的描述性名稱。  
  
3.  從**項目類型**下拉式功能表，選取此項目的類型。 可能的值包括：  
  
    |項目類型|Description|  
    |---------------|-----------------|  
    |商務里程碑|日期/時間值。 例如，訂單的核准日期。|  
    |商務資料 – TEXT|包含任何英數字元的字串。 例如，送貨至： 城市、 縣/市和郵遞區號的程式碼。|  
    |商務資料 - INTEGER|整數值。 例如，總訂購數。|  
    |商務資料 – Decimal|十進位值。 例如 PO 的總金額。|  
  
     如果您選取的項目輸入 「 商務資料-Text，您必須為中的字串輸入的字元數上限**最大長度**方塊。  
  
    > [!NOTE]
    >  如需有關建立這些項目的詳細資訊，請參閱 Microsoft BizTalk Server 教學課程中的＜夥伴管理與商務活動監控＞。  
  
4.  重複步驟 1 至 3，視需要新增所需的項目至這個活動。  
  
5.  完成 [商務活動監控活動精靈] 之後，[商務活動監控檢視精靈] 便會自動啟動。  
  
 如需有關使用此精靈的詳細資訊，請參閱[定義 BAM 檢視](../core/defining-a-bam-view.md)。  
  
## <a name="see-also"></a>另請參閱  
 [定義 BAM 檢視](../core/defining-a-bam-view.md)   
 [在 Excel 中定義商務活動和檢視](../core/defining-business-activities-and-views-in-excel.md)