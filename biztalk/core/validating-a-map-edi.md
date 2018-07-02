---
title: 驗證對應 (EDI) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: caf58ecf-ed10-4c13-8d7d-e007b9158b0e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6cfe1394d82f4fedb57aacb40bad27c95de2a46
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993335"
---
# <a name="validating-a-map-edi"></a>驗證對應 (EDI)
您可以在設計階段驗證對應。 若要這樣做，您可以使用的 XML 工具延伸模組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]環境。 這項作業會產生兩個檔案：一個檔案包含對應的基礎 XSLT，一個檔案包含延伸模組物件。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-validate-a-map"></a>若要驗證對應  
  
1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟專案。 在 [方案總管] 中，將您要驗證的對應及其輸入和輸出訊息結構描述加入至該專案。  
  
   > [!NOTE]
   >  訊息結構描述位於底下的適當子資料夾[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 資料夾。 如需有關安裝的結構描述檔案的詳細資訊，請參閱 <<c0> [ 如何安裝 EDI 結構描述檔案](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550)。  
   > 
   > [!NOTE]
   >  您不必建置專案來驗證對應。  
  
2. 以滑鼠右鍵按一下方案總管 中的對應，然後按一下**驗證對應**。  
  
3. 確認 [輸出] 視窗中有指出作業成功的訊息。  
  
4. 請注意任何警告，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中已張貼**輸出**視窗。  
  
5. 在 [**輸出**] 視窗中，請注意輸出 XSLT 的路徑與名稱。 這個 XSL 檔案將和對應檔案同名，但是它會另外加上副檔名 XSL。 您可以按 CTRL，然後按一下連結，在 BizTalk 編輯器中顯示該 XSL 檔案。  
  
6. 在 [**輸出**] 視窗中，記下名稱和路徑的延伸模組物件 XML。 您可以按 CTRL，然後按一下連結，在 BizTalk 編輯器中顯示該 XSL 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [使用設計階段 XML 工具](../core/using-design-time-xml-tools.md)