---
title: 產生執行個體 (EDI) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 362b9803-4d4a-4d17-9ad6-439ec4c7d8aa
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82674b175ad1c408b6ddb9f7823427a550288e96
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999295"
---
# <a name="generating-an-instance-edi"></a>產生執行個體 (EDI)
您可以在設計階段從 EDI 結構描述產生訊息執行個體。 若要執行此動作，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 XML 工具延伸模組。  
  
 您可以產生完整的批次交換 (含交換和群組標頭) 或交易集 (不含交換和群組標頭)。 如果您執行此作業產生完整的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會產生一個交換標頭、 群組，以針對每個結構描述，與每個群組的三個相同的交易集的檔案，每個結構描述。 如果您執行此作業產生交易集，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會產生含有單一交易集的檔案。  
  
 若要產生完整的批次交換，您可以在批次結構描述上執行 generate-instance 命令。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在專案中，會偵測到的訊息結構描述，並會自動包含這些結構描述的交易集。  
  
 若要產生單一交易集，您可以在訊息結構描述上執行 generate-instance 命令。 在此情況下，不需要將批次結構描述加入專案中。 產生的執行個體將不會包含交換或群組標頭，不過也因此您將需要手動加入它們，EDI 交換才能運作。  
  
 當您產生執行個體，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]顯示的對話方塊，您可以在其中指定該執行個體，包括分隔符號和語法識別項中使用的組態。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-generate-an-instance-of-a-batched-interchange"></a>產生批次交換的執行個體  
  
1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟專案。 在 [方案總管] 中，針對您要讓訊息結構描述包含的每一種交易集類型，新增訊息結構描述至專案。 新增至專案的編碼類型的批次結構描述： Edifact_BatchSchema.xsd 或 X12_BatchSchema.xsd。  
  
   > [!NOTE]
   >  批次結構描述位於[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 資料夾。  
   > 
   > [!NOTE]
   >  您不必建置專案來產生執行個體。  
  
2. 以滑鼠右鍵按一下方案總管 中的批次結構描述，然後按一下**屬性**。  
  
3. 在 **屬性**視窗中，將**產生的執行個體輸出類型**來**原生**或**XML**。 選取**原生**將會提示產生副檔名為.txt 的一般檔案。 選取**XML**將會提示產生 XML 檔案。  
  
4. 針對**輸出執行個體檔案名稱**、 輸入名稱或瀏覽至檔案以及選取的檔案。  
  
   > [!NOTE]
   >  如果您未針對輸出執行個體名稱輸入值，則會自動選取一個值。 檔案名稱將會顯示在 [輸出] 視窗的[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
   > 
   > [!NOTE]
   >  如果您選取現有的檔案，則現有檔案的內容將會取代為此作業產生的內容。  
  
5. 以滑鼠右鍵按一下 批次結構描述，然後按一下**產生的執行個體**。  
  
6. 在  **EDI 執行個體屬性**對話方塊中，選取分隔符號、 識別碼和其他設定選項以用於該執行個體，然後按一下**確定**。  
  
7. 確認作業從事**輸出**視窗。  
  
8. 若要檢視檔案，請按**控制**，然後按一下在連結**輸出**視窗。 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 在 [BizTalk 編輯器] 視窗中，將會顯示檔案的內容。  
  
   > [!NOTE]
   >  產生時包含 837I、 837 D 或 837p 的執行個體，GS08 的值會不正確地設定為 00401。 如需詳細資訊，請參閱 <<c0> [ 已知問題與 EDI 解決方案的 XML 工具搭配](../core/known-issues-with-xml-tools-used-with-edi-solutions.md)。  
  
### <a name="to-generate-an-instance-of-a-transaction-set"></a>產生交易集執行個體  
  
1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟專案。 針對要產生其執行個體的交易集類型新增結構描述。  
  
   > [!NOTE]
   >  您不必新增批次結構描述至專案，以產生交易集的執行個體。  
  
   > [!NOTE]
   >  您不必建置專案來產生執行個體。  
  
2. 以滑鼠右鍵按一下方案總管 中的訊息結構描述，然後按一下**屬性**。  
  
3. 在 [屬性] 視窗中，設定**產生的執行個體輸出類型**要**原生**或是**XML**。 選取**原生**將會提示產生副檔名為.txt 的一般檔案。 選取**XML**將會提示產生 XML 檔案。  
  
4. 針對**輸出執行個體檔案名稱**、 輸入名稱或瀏覽至檔案以及選取的檔案。  
  
   > [!NOTE]
   >  如果您未針對輸出執行個體名稱輸入值，則會自動選取一個值。 檔案名稱將會顯示在**輸出**窗口[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
   > 
   > [!NOTE]
   >  如果您選取現有的檔案，則現有檔案的內容將會取代為此作業產生的內容。  
  
5. 以滑鼠右鍵按一下訊息結構描述，然後按一下**產生的執行個體**。  
  
6. 在  **EDI 執行個體屬性**對話方塊中選取的組態選項，您想要，然後按一下**確定**。  
  
7. 確認中的訊息**輸出**指出作業成功的視窗。  
  
8. 若要檢視檔案，請按**控制**並按一下 [輸出] 視窗中的連結。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在 [BizTalk 編輯器] 視窗中，將會顯示檔案的內容。  
  
9. 若要讓 EDI 訊息運作，請在文字編輯器中新增交換和群組標頭至訊息。  
  
## <a name="see-also"></a>另請參閱  
 [使用設計階段 XML 工具](../core/using-design-time-xml-tools.md)   
 [驗證執行個體 (EDI)](../core/validating-an-instance-edi.md)