---
title: 步驟 2： 使用 Siebel 配接器在 BizTalk Server 管理主控台設定協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41338723-055d-46b4-acee-6969ea79fac0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f779c9b347c43fb9bd2a6dcdbdb3c33ac8ad09c5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009127"
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-with-the-siebel-adapter"></a>步驟 2： 使用 Siebel 配接器在 BizTalk Server 管理主控台設定協調流程
![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您可以執行下列工作：  
  
- 建立 WCF 自訂傳送-接收埠以傳送和接收來自 Siebel 系統使用的訊息[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 設定此連接埠使用您在上一個步驟中建立的對應。  
  
- 設定協調流程使用 WCF 自訂連接埠的最後一個步驟中部署。  
  
## <a name="prerequisite"></a>必要條件  
  
-   您必須部署 BizTalk 協調流程，您要設定 WCF 自訂連接埠。  
  
### <a name="to-create-a-wcf-custom-port"></a>若要建立一個 WCF 自訂連接埠  
  
1. 當您作業產生結構描述上 Siebel 系統使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，繫結檔案也會加入至 BizTalk 專案。 您可以將此繫結檔案匯入到您的 BizTalk 應用程式來建立 WCF 自訂傳送-接收埠。 如需匯入繫結檔案的指示，請參閱 <<c0> [ 匯入繫結](http://msdn.microsoft.com/library/908ab90c-2ba2-4c65-9f74-10579f06e372)。  
  
2. 匯入繫結檔案之後下, 建立傳送埠**傳送埠**在 BizTalk Server 管理主控台中的資料夾。  
  
3. 以滑鼠右鍵按一下 WCF 自訂連接埠，然後按一下**屬性**。  
  
4. 從傳送埠的 屬性 對話方塊的左窗格中，按一下**一般** 索引標籤。從右窗格中，按一下**設定**。  
  
5. 在 [ **Wcf-custom 傳輸屬性**] 對話方塊中，按一下**認證**索引標籤，然後指定要連接至 Siebel 系統的認證。  
  
6. 按一下 [確定] 。  
  
7. 從傳送埠的 [屬性] 對話方塊的左窗格中，按一下**輸入對應**。 從右窗格中，按一下 下的欄位**地圖**資料行，然後從下拉式清單中選取**ResponseMap**。  
  
    ![設定輸入的對應](../../adapters-and-accelerators/adapter-siebel/media/e1ceee98-9f10-40f1-a611-88d3a2c102a9.gif "e1ceee98-9f10-40f1-a611-88d3a2c102a9")  
  
8. 從傳送埠的 [屬性] 對話方塊的左窗格中，按一下**輸出對應**。 從右窗格中，按一下 下的欄位**地圖**資料行，然後從下拉式清單中選取**RequestMap**。  
  
    ![設定輸出對應](../../adapters-and-accelerators/adapter-siebel/media/8f8efeaa-d5cd-4ed3-b2f3-a600c48c3bb9.gif "8f8efeaa-d5cd-4ed3-b2f3-a600c48c3bb9")  
  
9. 按一下 [確定] 。  
  
### <a name="to-configure-the-biztalk-application"></a>若要設定的 BizTalk 應用程式  
  
1. 在 BizTalk Server 管理主控台中，依序展開**BizTalk 群組**，展開**應用程式**、 展開協調流程的部署位置的 BizTalk 應用程式。  
  
2. 以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。  
  
3. 從左窗格中，按一下 協調流程設定。 從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。  
  
4. 底下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應至 BizTalk Server 管理主控台中的實體連接埠。  
  
   1. 選取您將會卸除要求訊息的檔案連接埠。 BizTalk 協調流程將會取用的要求訊息，並將它傳送至 Siebel 系統。  
  
   2. 選取 BizTalk 協調流程將會卸除包含來自 Siebel 系統的回應的回應訊息的檔案連接埠。  
  
   3. 選取您稍早在本主題中建立 Wcf-custom 傳送埠。  
  
   4. 按一下 [確定] 。  
  
      設定應用程式的詳細資訊，請參閱 「 如何設定應用程式 」，網址[ http://go.microsoft.com/fwlink/?LinkId=102360 ](http://go.microsoft.com/fwlink/?LinkId=102360)。  
  
## <a name="next-steps"></a>後續步驟  
 您現在已完成移轉至 BizTalk 專案，將訊息傳送至使用 WCF 型 Siebel 系統 vPrev BizTalk 專案的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 您現在必須測試已移轉的 BizTalk 應用程式傳送到叫用的帳戶商務元件的 Insert 作業的要求訊息中所述[步驟 3： 測試移轉應用程式與 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/step-3-test-the-migrated-application-with-the-siebel-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 2： 移轉 BizTalk 專案中 Siebel](../../adapters-and-accelerators/adapter-siebel/tutorial-2-migrating-biztalk-projects-in-siebel.md)