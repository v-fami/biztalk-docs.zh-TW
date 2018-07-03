---
title: 驗證執行個體 (EDI) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0fe4e87-5ab4-41e4-8ceb-8f6cf40cae0b
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58150705b504193a527be729028b00d4384325d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993935"
---
# <a name="validating-an-instance-edi"></a>驗證執行個體 (EDI)
執行個體可以在設計階段時依據其 EDI 結構描述加以驗證。 若要執行此動作，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 XML 工具延伸模組。 進行驗證的執行個體可以是單一交易集 (不含交換和群組標頭)、包含單一交易集的交換 (含交換和群組標頭)，或是包含多個交易集的完整批次交換 (含交換和群組標頭)。  
  
> [!NOTE]
>  不支援 XML 保留交換的驗證作業， 但支援 EDI 保留交換的驗證作業。  
  
 這項驗證執行個體作業會執行 EDI 和 XSD 驗證。  
  
 當您驗證執行個體，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]顯示的對話方塊，您可以在其中指定要驗證該執行個體，包括分隔符號和語法識別項中的組態。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-validate-an-instance-against-its-schema"></a>若要依據具有的結構描述來驗證執行個體  
  
1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟專案。  
  
2. 在 [方案總管] 中，將訊息執行個體的所有必要結構描述加入至該專案中。  
  
   1. 若要驗證不含交換和群組標頭的單一交易集，請加入該交易集的文件結構描述。  
  
   2. 如果您要驗證單一交易集的交換，將新增至專案之交易的結構描述和訊息所使用的編碼類型的批次結構描述 (Edifact_BatchSchema.xsd 或 X12_BatchSchema.xsd 中的[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI)。  
  
      > [!NOTE]
      >  批次結構描述，才能驗證信封執行個體。 如果您是使用訊息結構描述，就不會驗證信封。  
  
   3. 如果您要驗證包含多個交易集的批次的交換，將新增至專案的結構描述代表每個交易集訊息執行個體和訊息所使用的編碼類型的批次結構描述中的群組 (任一 Edifact_BatchSchema.xsd 或在 X12_BatchSchema.xsd [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI)。  
  
      > [!NOTE]
      >  如果您有自訂的服務結構描述，這時除了文件 (交易集) 結構描述和可能需要的批次結構描述之外，您還必須將該自訂服務結構描述加入至 BizTalk 專案中。  
  
      > [!NOTE]
      >  您不一定要建置專案才能驗證執行個體。  
  
3. 在 [方案總管] 中，顯示結構描述的屬性頁，如下所示：  
  
   1.  如果您要驗證單一交易集，以滑鼠右鍵按一下該交易集的文件結構描述，然後按一下**屬性**。  
  
   2.  如果您要驗證單一交易集的交換或包含多個交易集的批次的交換，以滑鼠右鍵按一下 批次結構描述 （Edifact_BatchSchema.xsd 或 X12_BatchSchema.xsd 結構描述），然後再按一下**的屬性**.  
  
4. 針對結構描述中，屬性 視窗中的**輸入執行個體檔案名稱**輸入您想要驗證，或瀏覽至檔案並加以選取，然後按一下 訊息執行個體的路徑與名稱**確定**。  
  
5. 針對**驗證執行個體輸入類型**，輸入要驗證的檔案類型：**原生**EDI 檔案或**XML** XML 檔案。  
  
   > [!NOTE]
   >  不支援 XML 保留交換的驗證作業， 如果您選取 XML for**驗證執行個體輸入類型**屬性驗證保留的交換時，此作業會失敗，而且不會傳回。 不過，如果您選取**原生**for**驗證執行個體輸入類型**時驗證保留的交換，作業會成功。  
  
6. 以滑鼠右鍵按一下訊息結構描述 （Edifact_BatchSchema.xsd 或 X12_BatchSchema.xsd 若驗證包含單一交易集或批次的交換），然後按一下**驗證執行個體**。  
  
7. 在  **EDI 執行個體屬性**對話方塊方塊中，執行下列動作：  
  
   1.  如果您的執行個體應該使用重複分隔符號，選取**重複分隔符號**。  
  
   2.  如果您的執行個體應該使用尾端分隔符號，選取 **[是]** for**使用尾端分隔符號**。  
  
   3.  如果您的執行個體應該使用字元集以外**基本**，選取**擴充**或是**Unicode**中**語法識別項**。  
  
   4.  按一下 [確定] 。  
  
       > [!NOTE]
       >  **EDI 執行個體屬性** 對話方塊可能會出現第二次之後您已按下,**確定**。 如果是的話，按一下**確定**一次。  
  
       > [!NOTE]
       >  **EDI 執行個體屬性**對話方塊會填入相同的登入的使用者在上次執行的驗證執行個體作業中使用的相同值。  
  
8. 確認中的訊息**輸出**指出作業成功的視窗。  
  
## <a name="see-also"></a>另請參閱  
 [使用設計階段 XML 工具](../core/using-design-time-xml-tools.md)   
 [產生執行個體 (EDI)](../core/generating-an-instance-edi.md)