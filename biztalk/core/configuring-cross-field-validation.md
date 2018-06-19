---
title: 設定欄位交互驗證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f0c6ae8-0b8a-4826-9dfb-bf27e5ff7fa6
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bde88ac82d69cdaa0dec7513e294953b7164b56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233646"
---
# <a name="configuring-cross-field-validation"></a>設定欄位交互驗證
本主題說明如何在 EDI 編碼訊息內的交易集資料元素，啟用欄位/區段交互驗證。 若要這樣做，必須進行兩種設定：  
  
-   設定 EDI 結構描述註解中的欄位交互驗證旗標。 若為 X12 或 HIPAA 結構描述，則**X12ConditionDesignator_Check**旗標。 若為 EDIFACT 結構描述，則**EdifactDependencyRule_Check**旗標。  
  
-   啟用 在協議屬性中的 EDI 類型驗證。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="configuring-cross-field-validation"></a>設定欄位交互驗證  
  
1.  在 BizTalk 編輯器中開啟結構描述。  
  
2.  對於 X12 或 HIPAA 結構描述，尋找**X12ConditionDesignator_Check**註解的結構描述 appinfo 區段中的旗標。 將它設定為**是**。  
  
    > [!NOTE]
    >  設定的旗標 X12ConditionDesignator_Check**是**無法執行從 BizTalk 結構描述編輯器。 若要設定該旗標，必須在記事本或類似的文字編輯器中開啟結構描述檔案 (.xsd)，並且在編輯後儲存。  
  
3.  對於 EDIFACT 結構描述中，尋找**EdifactDependencyRule_Check**註解的結構描述 appinfo 區段中的旗標。 將它設定為**是**。  
  
4.  針對結構描述適用的區段，指定套用的關係條件 (X12 和 HIPAA) 或相依性規則 (EDIFACT)。 如需詳細資訊，請參閱[跨欄位區段驗證](../core/cross-field-segment-validation.md)。  
  
    > [!NOTE]
    >  針對 EDI 結構描述內的區段，輸入欄位交互驗證條件或規則。 如果您的資料元素，而不是在區段中，輸入欄位交互驗證規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行結構描述驗證時，會產生警告。  
  
5.  在**驗證**頁面 (下**交易集設定**區段) 的單向協議索引標籤**協議屬性**相關的協議 對話方塊請確定**EDI 類型驗證**選取屬性。  
  
## <a name="see-also"></a>另請參閱  
 [開發 EDI 結構描述](../core/developing-edi-schemas.md)