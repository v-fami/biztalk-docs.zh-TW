---
title: 步驟 5： 修改 Contoso 私用程序協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private processes, orchestrations
- private process tutorial, modifying private process orchestration
ms.assetid: a5430db8-e5f0-48a6-abb9-e268d8ec2ec4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 197854a1a37846a11b07b126ec73cb7f204d91b1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972895"
---
# <a name="step-5-modifying-the-contoso-private-process-orchestration"></a>步驟 5： 修改 Contoso 私用程序協調流程
在此步驟中，您將修改私用程序協調流程，以便與 Contoso 的「企業資源規劃」(Enterprise Resource Planning，ERP) 系統進行整合。 Contoso 的 ERP 系統使用內部定義的產品價格與可用性結構描述。 自訂「3A2 - 價格與可用性交易夥伴介面程序 (PIP)」的私用程序之後，您就能夠使用結構描述對應資訊與 ERP 系統進行整合。  
  
### <a name="to-add-a-reference-to-the-contoso-priceandavailability-and-rnpips-assemblies"></a>加入 Contoso PriceAndAvailability 及 RNPIPs 組件的參考  
  
1. Contoso 方案顯示在 [方案總管] 中，以滑鼠右鍵按一下**PrivateResponder**專案，然後再按一下**加入參考**。  
  
2. 在 [加入參考] 對話方塊中，按一下**瀏覽**。 移至*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\Bin 資料夾，然後選取下列組件<strong>:</strong>  
  
   -   Microsoft.Solutions.BTARN.CommonTypes.dll  
  
   -   Microsoft.Solutions.BTARN.ConfigurationManager.dll  
  
   -   Microsoft.Solutions.BTARN.GlobalSchemas.dll  
  
   -   Microsoft.Solutions.BTARN.PublicResponder.dll  
  
   -   Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll  
  
   -   Microsoft.Solutions.BTARN.Shared.dll  
  
   -   Microsoft.Solutions.BTARN.XSDClasses.GlobalSchemas.dll  
  
3. 按一下 **[加入]**。  
  
4. 在 [加入參考] 對話方塊中，按一下**專案**索引標籤上，選取**ContosoPriceAndAvailability**並**HeaderHelper**專案，然後再按一下**新增**。  
  
5. 按一下 [確定] 。  
  
6. 在 Microsoft 開發環境 對話方塊中，按一下**確定**。  
  
### <a name="to-create-new-message-types"></a>建立新訊息類型  
  
1.  在 [方案總管] 中，按兩下**PrivateResponder**協調流程加以開啟。  
  
2.  在 [方案總管] 中，按一下**協調流程檢視**。  
  
3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
4.  在 [屬性] 視窗中，在**識別碼**方塊中，輸入**PIP3A2RequestMessage**。  
  
5.  在**訊息類型**方塊中，按一下下拉箭號，展開**結構描述**，然後選取**\<從參考組件選取\>**。  
  
6.  在 選取成品類型 方塊中，選取**Microsoft.Solutions.BTARN.Schemas.RNPIPs**的左窗格中，選取 **_3a2priceandavailabilityquerymessageguideline_v1_3**在右窗格中，並然後按一下**確定**。  
  
7.  重複執行步驟 3 至 6，使用下列資訊建立方案的所有訊息類型：  
  
    |識別碼|組件|訊息類型|  
    |----------------|--------------|------------------|  
    |PIP3A2ResponseMessage|Microsoft.Solutions.BTARN。<br />Schemas.RNPips|_3A2PriceAndAvailability<br />ResponseMessageGuideline_v1_3|  
    |Contoso3A2ResponseMessage|ContosoPriceAndAvailability|rootPriceResponse|  
    |Contoso3A2RequestMessage|ContosoPriceAndAvailability|rootPriceRequest|  
  
8.  您已經完成建立方案的訊息類型。  
  
### <a name="to-create-new-variables"></a>建立新變數  
  
1.  在協調流程檢視中，以滑鼠右鍵按一下**變數**，然後按一下**新變數**。  
  
2.  在 [屬性] 視窗中，在**識別碼**方塊中，輸入**contosoResponseXML**。  
  
3.  在 **型別**方塊中，選取 **\<.NET 類別\>** 從下拉式清單。  
  
4.  在 [選取成品類型] 對話方塊，在左窗格中，底下**目前的專案**並**參考**節點，選取**System.Xml**，選取**XmlDocument**從清單中，在右窗格中，然後按一下 **[確定]**。  
  
5.  在 **協調流程檢視**，按一下**變數**，然後按一下**新變數**。  
  
6.  在 [屬性] 視窗中，在**識別碼**方塊中，輸入**submitMessage**。  
  
7.  在 **型別**方塊中，選取 **\<.NET 類別\>** 從下拉式清單。  
  
8.  在 [選取成品類型] 對話方塊中，在左窗格中，展開**目前的專案**並**參考**節點，選取**再**，選取**SubmitRNIF**從清單中，在右窗格中，然後按一下 **[確定]**。  
  
### <a name="to-change-the-orchestration-filter-expression"></a>變更協調流程的篩選條件運算式  
  
1.  在協調流程設計師中，選取**ReceiveFromPublicProcessResponder**圖形。  
  
2.  在 [屬性] 視窗中，在**篩選條件運算式**方塊中，按一下 [值] 方塊中，，然後按一下省略符號按鈕 (**...**) 以開啟 [篩選運算式] 對話方塊。  
  
3.  在 [篩選運算式] 對話方塊中，在**Group By**區段中，按一下**或者**值的第一行，然後按**AND**從下拉式清單。  
  
4.  在 [篩選運算式] 對話方塊中，按一下**按一下這裡以加入新的資料列**，然後選取**Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode**從下拉式清單。  
  
5.  在相同的資料列，按一下**值**，然後輸入 **"3A2"**。  
  
6.  在相同的資料列，按一下**AND**中**Group By**方塊，然後按**或**從下拉式清單。  
  
7.  在 [篩選條件運算式] 對話方塊中，選取剛才建立的那一列，然後按一下向上箭號按鈕，將該列上移一列。  
  
8.  按一下 **按一下這裡以加入新的資料列**，然後選取**Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode**從下拉式清單。  
  
9. 在相同的資料列，按一下**值**，然後輸入 **"3A2"**。  
  
10. 按一下 [確定]。  
  
### <a name="to-modify-the-business-process-workflow"></a>修改商務程序工作流程  
  
1. 拖曳**訊息指派**圖形從工具箱拖曳至設計介面，然後放在**ReceiveFromPublicProcessResponder**圖形。 選取  **constructmessage_1**所建立的圖形並在**屬性**視窗中**名稱**方塊中，輸入**ConstructPIP3A2RequestMessage**.  
  
2. 拖曳**轉換**圖形至設計介面，然後放在**ConstructPIP3A2RequestMessage**圖形。 選取  **constructmessage_1**所建立的圖形並在**屬性**視窗中**名稱**方塊中，輸入**ConstructContoso3A2RequestMessage**.  
  
3. 拖曳**傳送**圖形至設計介面，然後放在**ConstructContoso3A2RequestMessage**圖形。  
  
4. 拖曳**接收**圖形至設計介面，然後放在**Send_1**圖形。  
  
5. 按一下協調流程設計介面的空白區域。  
  
6. 在 [屬性] 視窗中，選取**交易類型**屬性，，然後按一下**長時間執行**。  
  
7. 拖曳**領域**圖形至設計介面，然後放在**Receive_1**圖形。  
  
8. 在 [屬性] 視窗中，從**交易類型**屬性下拉式清單中，選取**不可部分完成**for**範圍**圖形。  
  
9. 拖曳**呼叫規則**圖形至設計介面並放置在標籤**從 [工具箱] 拖曳圖形**內**範圍**圖形。 在 [屬性] 視窗**呼叫規則**圖形，在**名稱**方塊中，輸入**Execute3A2Vocabulary**。  
  
10. 拖曳**轉換**圖形至設計介面，然後放在**Scope_1**圖形。 按一下  **constructmessage_1**圖形。 在 [屬性] 視窗中，在**名稱**方塊中，輸入**Construct3A2ResponseMessage**。  
  
11. 拖曳**運算式**圖形至設計介面，然後放在**Construct3A2ResponseMessageTransform**圖形。  
  
12. 在 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**，按一下 **全部儲存**以儲存專案。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 6：設定協調流程圖形 (Contoso)](../../adapters-and-accelerators/accelerator-rosettanet/step-6-configuring-orchestration-shapes-contoso.md)