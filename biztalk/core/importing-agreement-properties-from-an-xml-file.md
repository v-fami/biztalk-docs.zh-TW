---
title: "從 XML 檔案匯入協議屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8bf5268-1742-47da-b42f-6472706a9bff
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc0bd397e49dcad670bb73e9dff9c164b9d0997a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="importing-agreement-properties-from-an-xml-file"></a>從 XML 檔案匯入協議屬性
本節提供如何從 XML 範本檔案匯入協議屬性的指示。  
  
## <a name="prerequisites"></a>必要條件  
 以下是執行此主題中之程序的必要條件：  
  
-   您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
-   您必須匯出協議至 XML 範本檔案中所述[將協議屬性匯出至 XML 檔案](../core/exporting-agreement-properties-to-an-xml-file.md)。  
  
### <a name="to-import-agreement-properties-from-an-xml-file"></a>若要從 XML 檔案匯入協議屬性  
  
1.  在 BizTalk Server 管理主控台中，按一下 **合作對象**節點下的**BizTalk Server 管理**和**BizTalk 群組**節點。 在**合作對象與商務設定檔**頁面上，依照建立協議[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。  
  
2.  在**協議屬性**對話方塊中，按一下 **從範本載入**。  
  
    > [!NOTE]
    >  **從範本載入**選取協議的通訊協定之後，才會啟用按鈕。 當您指定通訊協定時，您也同時隱含地宣告了您只能為匯入相同編碼通訊協定的協議。  
  
3.  在**開啟**對話方塊中，瀏覽至 XML 範本檔案的位置選取檔案，然後按一下 **開啟**。  
  
4.  在**建立範本**方塊中，按一下**確定**。  
  
## <a name="see-also"></a>請參閱  
 [重複使用另一個協議屬性](../core/reusing-properties-from-another-agreement.md)   
 [將協議屬性匯出至 XML 檔案](../core/exporting-agreement-properties-to-an-xml-file.md)