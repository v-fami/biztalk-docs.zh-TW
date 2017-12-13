---
title: "使用新的 PIP 擴充 BTARN |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTARN, extending functionality
- PIPs, extending BTARN
- BTARN, PIPs
ms.assetid: 3db5cd5c-031f-4451-9be5-4b5d6163c3b1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2b1fca61cd40b932e53b2908603a225d3980fa1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="extending-btarn-with-a-new-pip"></a>使用新的 PIP 擴充 BTARN
本主題說明如何擴充[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]與新的交易夥伴介面程序 (PIP) 結構描述。 當該 PIP 未與任何由 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 安裝程式安裝的結構描述關聯時，這可以讓您根據 RosettaNet PIP 新增結構描述。  
  
 當您使用新的 PIP 擴充 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 時，便會在這個新結構描述本身的組件中部署這個結構描述。 此外，您也可以修改 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] RNPIP 組件內所部署的現有結構描述。 如需詳細資訊，請參閱[修改 Rnpip 中的現有 PIP](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)。  
  
### <a name="to-extend-btarn-with-a-new-pip"></a>使用新的 PIP 擴充 BTARN  
  
1.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
2.  在命令提示字元中，移至\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator for RosettaNet\SDK\Utilities\Schema Generator。  
  
3.  在命令提示字元中，輸入**CScript InstallDTD.vbs**，然後按下**Enter**。  
  
    > [!NOTE]
    >  您只必須在安裝 BizTalk Server 後，一次執行步驟 1 到 3。  
  
4.  啟動 Visual Studio。  
  
5.  在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。  
  
6.  在 新增專案 對話方塊中，選取  **BizTalk 專案**在左的窗格中，然後按一下**空白 BizTalk Server 專案**右窗格中。  
  
7.  按一下**瀏覽**點指派到您要儲存專案的目錄。  
  
8.  在**名稱**方塊中，輸入專案名稱，例如**MyCustomPIP**，然後按一下 **確定**。  
  
9. 啟動 Visual Studio 命令提示字元。  
  
10. 在命令提示字元中，移至步驟 7 中，型別中輸入位置**sn-k\<專案 name.snk\>**，然後按下**Enter**。  
  
11. 在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**屬性**。  
  
12. 在**屬性頁**對話方塊中，按一下 **組件**下**通用屬性**的左窗格中。  
  
13. 在右窗格中，向下捲動至**強式名稱**，按一下 **組件金鑰檔案**，然後按一下右窗格中的省略符號按鈕 （...）。 移至在步驟 7 中輸入的位置，然後選取在步驟 10 中建立的 .snk 檔案名稱。  
  
14. 在 屬性頁 對話方塊中，依序展開**組態屬性**，然後按一下 **部署**。 在右窗格中，按一下 **重新部署**，選取`True`，然後按一下 **確定**。  
  
15. 在 方案總管 中，以滑鼠右鍵按一下專案名稱，指向**新增**，然後按一下 **現有項目**。  
  
16. 在**加入現有項目**對話方塊中，移至\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator for RosettaNet\SDK\Schemas，選取**xml.xsd**，然後按一下 **新增**。  
  
17. 從 RosettaNet.org 下載您要用來擴充 RNPIP 的 PIP。如需詳細資訊，請參閱[納入新的交易夥伴介面程序](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)。  
  
18. 在 方案總管 中，展開 專案名稱，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。  
  
19. 在**加入參考**對話方塊中，按一下 **瀏覽**，並移至\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk 2013 Accelerator for RosettaNet\Bin，然後選取**Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll**。 按一下**開啟**，然後按一下 **確定**。  
  
20. 在 方案總管 中，以滑鼠右鍵按一下專案名稱，指向**新增**，然後按一下 **新增產生的項目**。  
  
21. 在**新增產生的項目**對話方塊中，於**類別**] 窗格中，按一下 [**產生結構描述**。 在**範本** 窗格中，按一下 **產生結構描述**，然後按一下 **新增**。  
  
22. 在 [產生結構描述] 對話方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**文件類型**|選取**DTD 結構描述**。|  
    |**輸入的檔**|按一下**瀏覽**、 移至含有從 RosettaNet.org 的 DTD 檔案的資料夾、 選取的 DTD 檔案，然後再按一下**開啟**。|  
  
23. 在 [產生結構描述] 對話方塊中，按一下**確定**。  
  
24. 在 [方案總管] 中，按兩下剛匯入的 .xsd 檔。  
  
25. 在 [BizTalk 編輯器] 中，選取\<*結構描述*\>節點。  
  
26. 在 [屬性] 視窗中向下捲動至**文件類型**。 在**文件類型** 方塊中， **PIP**\<*三位數代碼*\>，例如**PIP3A2**。 在**文件版本**方塊中，輸入**v**\<*xx.xx* \>或**R** \< *xx.xx*\>，例如**R01.02**。 請依照 RosettaNet PIP 規格記載的方式輸入這個版本。  
  
27. 在 [屬性] 視窗中向下捲動至**根參考**。 按一下**根參考**，然後從下拉式清單中，選取根節點的結構描述，例如，選取**Pip3C5BillingStatementNotification**。  
  
28. 在 [屬性] 視窗中，向上捲動至**目標命名空間**。 如**目標命名空間**，型別**http://schemas.microsoft.com/biztalk/btarn/2004/\<DTD 檔案名稱\>.dtd**，其中的 DTD 檔案名稱是，比方說， **3C5_MS_R01_00_BillingStatementNotification.dtd**。  
  
    > [!NOTE]
    >  BTARN 的目標命名空間必須採用這個命名慣例。 如果您使用其他命名空間慣例，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將無法處理 PIP 文件來進行結構描述驗證。  
  
    > [!NOTE]
    >  目標命名空間屬性中的 DTD 檔案名稱包括了 PIP 的版本號碼。 這讓您可以使用同一組 PIP 代碼的多重版本。  
  
29. 在 [屬性] 視窗中，向上捲動至**匯入**。 按一下旁邊的省略符號按鈕 （...）**匯入**，然後按一下 **新增**。  
  
30. 在**BizTalk 型別選擇器**對話方塊方塊中，展開  \<*專案名稱*\>，依序展開**參考**，依序展開**Microsoft.Solutions.BTARN.Schemas.RNPIPs**，依序展開**結構描述**，選取**Microsoft.Solutions.BTARN.Schemas.RNPIPs.BaseDataTypes**，按一下  **確定**，然後按一下 **確定**一次。  
  
31. 以滑鼠右鍵按一下專案名稱，然後**部署**。  
  
32. 按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
33. 在 BizTalk 管理主控台中，依序展開**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **（本機）**，然後展開**主機**。 在下**主機**，按一下  **BizTalkServerApplication**。  
  
34. 在右窗格中，主機名稱上按一下滑鼠右鍵，然後按一下 **重新啟動**。  
  
    > [!NOTE]
    >  使用剛匯入的 PIP 擴充 RNPIP 之後，您必須在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中，建立正確的 PIP 組態以及使用該 PIP 的協議。  
  
## <a name="see-also"></a>請參閱  
 [加入新的交易夥伴介面程序](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)   
 [使用 Pip](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md)   
 [修改 RNPIP 中的現有 PIP](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)