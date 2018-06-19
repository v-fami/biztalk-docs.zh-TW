---
title: 設定驗證 （X12-交易集設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0245be7f-d212-43b1-bfef-cbcbd851b5c0
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 880a8d1e31cbb10f570dcf5e7422a1e61b5cc8d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234262"
---
# <a name="configuring-validation-x12-transaction-set-settings"></a>設定驗證 (X12 交易集設定)
交易集驗證設定可定義 BizTalk Server 如何驗證接收自合作對象的交易集。 在驗證設定中，您可以指定 BizTalk Server 會在內送交換上執行的驗證類型。  
  
> [!NOTE]
>  本主題也適用於 HIPAA 驗證設定。  
  
> [!IMPORTANT]
>  任何屬性已停用此頁面上即使您清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-validation-settings"></a>若要設定驗證設定  
  
1.  建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交易集設定**區段中，按一下**驗證**。  
  
3.  在格線中，您可以針對不同的交易集定義不同的驗證設定。 在**驗證**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**預設值**|選取此核取方塊可定義預設驗證設定。|  
    |**交易類型**|按一下此欄中的空白儲存格，然後從下拉式清單中選取交易類型。|  
    |**Edi 類型驗證**|選取此選項，啟用對交換接收者的 EDI (資料元素) 驗證。 這項驗證會針對交易集資料元素、驗證資料型別、長度限制，以及空的資料元素和培訓分隔符號執行 EDI 驗證。 如需詳細資訊，請參閱[EDI 類型 （資料元素） 驗證](../core/edi-type-data-element-validation.md)。 **注意：** 如果它已在結構描述註解，即使未選取此屬性，仍執行欄位/區段交互驗證。|  
    |**擴充的驗證**|如果選取此選項，可針對從交換傳送者所接收的交換，啟用擴充 (BizTalk XSD) 驗證。 除了 XSD 資料型別驗證外，還包括欄位長度、選用性和重複計數驗證。 如需詳細資訊，請參閱[擴充 (BTS-XSD) 驗證](../core/extended-bts-xsd-validation.md)。 **注意：** 您可以選取此核取方塊才**Edi 類型驗證**已選取。|  
    |**允許前置和尾端零及空格**|如果選取此方塊，可指定如果 EDI 交換中的資料項目由於開頭或尾端有零或空格而不符合其長度需求，但在移除這些項目之後就符合長度需求時，從合作對象所接收的 EDI 交換會通過驗證。 **注意：** 您可以選取此核取方塊才**Edi 類型驗證**已選取。|  
    |**尾端分隔符號原則**|-選取**不允許**如果您不想允許在從交換傳送者所接收之交換中使用尾端分隔符號與分隔字元。 如果此交換包含尾端分隔符號，此交換即宣告無效。<br />-選取**選擇性**接受具有或不具有結尾分隔字元的交換。<br />-選取**強制**如果收到的交換必須包含尾端分隔符號與分隔字元。|  
  
     您可以新增任意多個資料列，以定義特定交換的驗證設定。  
  
     若要刪除驗證設定，請選取資料列，然後按一下**刪除**。  
  
    > [!NOTE]
    >  在格線中編輯屬性可能有點困難。 相反地，您可以選取要編輯，然後編輯中的相同屬性的資料列**編輯選取的資料列**> 一節。 您在此提供的設定會反映在選取的資料列中。  
  
4.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交易集設定 (X12)](../core/configuring-transaction-set-settings-x12.md)