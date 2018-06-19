---
title: 修改 Rnpip 中的現有 PIP |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RNPIPs
- modifying, PIPs
- PIPs, modifying
- assemblies, RNPIPs
ms.assetid: f2ed25c4-1979-4691-9315-e7568e7cca8b
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce7f87d9af24e6388199e76e9cbf0eba076ceacf
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006287"
---
# <a name="modifying-an-existing-pip-in-rnpips"></a>修改 Rnpip 中的現有 PIP
本主題描述如何變更和重新部署所安裝的交易夥伴介面程序 (PIP) 結構描述的其中一個[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]安裝程式。 您可將該結構描述部署為 RNPIP 組件的一部分。  
  
### <a name="to-modify-an-existing-pip-in-rnpips"></a>修改 RNPIP 中的現有 PIP  
  
1.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
2.  找出\<*磁碟機*\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\Utilities\Schema Generator 資料夾。  
  
3.  在命令提示字元中，輸入**CScript InstallDTD.vbs**，然後按 ENTER 鍵。  
  
    > [!NOTE]
    >  您只需要執行步驟 1 和 2 一次之後您安裝 BizTalk Server。  
  
4.  啟動**Microsoft Visual Studio 2012**。  
  
5.  在**檔案**功能表上，指向**開啟**，然後按一下 **專案**。  
  
6.  在**開啟專案**對話方塊中，移至\<*磁碟機*\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\結構描述，然後選取**RNPIPs.btproj**。  
  
7.  在**檢視**功能表上，按一下  **BizTalk 總管**。 展開**組件**，然後以滑鼠右鍵按一下**microsoft.solutions.btarn.schemas.rnpips （3.3.0.0)**。 按一下**解除部署**。  
  
8.  啟動**Visual Studio 2012 的命令提示字元**。  
  
9. 移至的位置，在命令提示字元，輸入在步驟 6 中輸入**sn-k RNPIPs.snk**，然後按下**Enter**。  
  
10. 在 方案總管 中，以滑鼠右鍵按一下**Rnpip**，按一下 **屬性**，按一下 **通用屬性**，然後按一下 **組件。**  
  
11. 在右窗格中，向下捲動至**強式名稱**，請在**組件金鑰檔案**區段中，按一下省略符號按鈕 （...） 按鈕，移至在命令提示字元，輸入在步驟 6 中輸入的位置**RNPIPs.snk**，然後按一下 **確定**。  
  
12. 在**屬性頁**對話方塊中，按一下 **組態屬性**，按一下 **部署**，按一下 **重新部署**，選取`True`，然後按一下 **確定**。  
  
13. 依需要編輯 RNPIP 中的任何現有結構描述。  
  
14. 按一下**檔案**，然後按一下 **儲存**。  
  
15. 以滑鼠右鍵按一下專案名稱，然後**建置**。  
  
16. 以滑鼠右鍵按一下專案名稱，然後**部署**。  
  
17. 按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
18. 在 BizTalk 管理主控台中，依序展開**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **（本機）**，然後展開**主機**。  
  
19. 在右窗格中，主機名稱上按一下滑鼠右鍵，然後按一下 **停止**。 服務已停止之後，以滑鼠右鍵按一下主控件名稱，然後按一下**啟動**。  
  
## <a name="see-also"></a>請參閱  
 [程式設計手冊](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)   
 [整合新的交易夥伴介面程序](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)