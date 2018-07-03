---
title: 步驟 2： 設定協調流程中使用 Oracle 資料庫配接器的 BizTalk Server 管理主控台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 598b4ab0-ff22-4dfa-aa9c-774c60c90227
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e0a8b8035b27babeacd6e5ade8c2cc40c8af2d75
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007863"
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-to-use-the-oracle-database-adapter"></a>步驟 2： 設定協調流程中使用 Oracle 資料庫配接器的 BizTalk Server 管理主控台
![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您可以執行下列工作：  
  
- 建立 WCF 自訂傳送-接收埠以傳送和接收訊息，從 Oracle 資料庫使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 設定此連接埠使用您在上一個步驟中建立的對應。  
  
- 設定協調流程使用 WCF 自訂連接埠的最後一個步驟中部署。  
  
## <a name="prerequisite"></a>必要條件  
  
-   您必須部署 BizTalk 協調流程，您要設定 WCF 自訂連接埠。  
  
### <a name="to-create-a-wcf-custom-port"></a>若要建立一個 WCF 自訂連接埠  
  
1. 當您作業產生結構描述在 Oracle 資料庫使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，繫結檔案也會加入至 BizTalk 專案。 您可以將此繫結檔案匯入到您的 BizTalk 應用程式來建立 WCF 自訂傳送-接收埠。 如需匯入繫結檔案的指示，請參閱 <<c0> [ 匯入繫結](http://msdn.microsoft.com/library/4cac9267-8bd8-453b-96b4-5c038912463f)。  
  
2. 匯入繫結檔案之後下, 建立傳送埠**傳送埠**在 BizTalk Server 管理主控台中的資料夾。  
  
3. 以滑鼠右鍵按一下 WCF 自訂連接埠，然後按一下 **屬性**。  
  
4. 從傳送埠的 屬性 對話方塊的左窗格中，按一下**一般** 索引標籤。從右窗格中，按一下**設定**。  
  
5. 在 [ **Wcf-custom 傳輸屬性**] 對話方塊中，按一下**認證**索引標籤，然後指定要連接到 Oracle 資料庫的認證。  
  
6. 按一下 [確定] 。  
  
7. 從傳送埠的 [屬性] 對話方塊的左窗格中，按一下**輸入對應**。 從右窗格中，按一下 下的欄位**地圖**資料行，然後從下拉式清單中選取**ResponseMap**。  
  
    ![設定輸入的對應](../../adapters-and-accelerators/adapter-oracle-database/media/a5e49da1-fe34-46fe-80ca-9316d217171a.gif "a5e49da1-fe34-46fe-80ca-9316d217171a")  
  
8. 從傳送埠的 [屬性] 對話方塊的左窗格中，按一下**輸出對應**。 從右窗格中，按一下 下的欄位**地圖**資料行，然後從下拉式清單中選取**RequestMap**。  
  
    ![設定輸出對應](../../adapters-and-accelerators/adapter-oracle-database/media/697b23d8-4231-4718-8a52-8013fac35e3e.gif "697b23d8-4231-4718-8a52-8013fac35e3e")  
  
9. 按一下 [確定] 。  
  
### <a name="to-configure-the-biztalk-application"></a>若要設定的 BizTalk 應用程式  
  
1. 在 BizTalk Server 管理主控台中，依序展開**BizTalk 群組**，展開**應用程式**、 展開協調流程的部署位置的 BizTalk 應用程式。  
  
2. 以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。  
  
3. 從左窗格中，按一下 協調流程設定。 從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。  
  
4. 底下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應至 BizTalk Server 管理主控台中的實體連接埠。  
  
   1. 選取您將會卸除要求訊息的檔案連接埠。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 Oracle 資料庫。  
  
   2. 選取 BizTalk 協調流程將會卸除包含從 Oracle 資料庫回應的回應訊息的檔案連接埠。  
  
   3. 選取您稍早在本主題中建立 Wcf-custom 傳送埠。  
  
   4. 按一下 [確定] 。  
  
      設定應用程式的詳細資訊，請參閱 「 如何設定應用程式 」，網址[ http://go.microsoft.com/fwlink/?LinkID=196961 ](http://go.microsoft.com/fwlink/?LinkID=196961)。  
  
## <a name="next-steps"></a>後續步驟  
 您現在已完成移轉至 BizTalk 專案，將訊息傳送到使用以 WCF 為基礎的 Oracle 資料庫 vPrev BizTalk 專案的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 您現在必須測試已移轉的 BizTalk 應用程式傳送要求訊息至執行的 Oracle 資料庫上，插入作業中所述[步驟 3： 測試已移轉的應用程式，到 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/step-3-test-the-migrated-application-to-oracle-database-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程： 移轉 BizTalk 專案](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)