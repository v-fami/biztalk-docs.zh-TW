---
title: 步驟 3： 設定並啟動應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4252470-805e-404f-80d5-df8d1ff3af63
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f932ca1f3570f080de239dd90c52d9a5f5db721
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988199"
---
# <a name="step-3-configure-and-start-the-application"></a>步驟 3： 設定並啟動應用程式
![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您會設定及啟動 SampleApplication 應用程式。 當您設定 SampleApplication 應用程式時，您將建立關聯的邏輯的成品，您在建立[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]與其實體對應項目。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[步驟 2： 設定的連接埠](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md)。  
  
### <a name="to-configure-and-start-the-application"></a>若要設定及啟動應用程式  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 在左邊的主控台樹狀目錄中，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**重新整理**。  
  
3. 依序展開**BizTalk 群組**，展開**應用程式**，以滑鼠右鍵按一下**SampleApplication**，然後按一下**設定**。  
  
4. 在 **設定應用程式**對話方塊的  **EmployeeOrch**索引標籤上，執行下列動作：  
  
   1.  針對**主機**下拉式清單中，選取**BizTalkServerApplication**。  
  
   2.  按兩下資料格跨越**ReceiveNotification** ，然後選取**NotifyReceivePort**從下拉式清單。  
  
   3.  按兩下資料格跨越**SQLOutboundPort** ，然後選取**SQLOutboundPort**從下拉式清單。  
  
   4.  按兩下資料格跨越**SaveResponsePort** ，然後選取**EmailResponse**從下拉式清單。  
  
5. 下圖顯示設定的應用程式。  
  
    ![設定應用程式](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-011-configure-app.gif "sql_adap_tut_011_configure_app")  
  
6. 在 [**設定應用程式**] 對話方塊中，按一下**確定**。  
  
7. 在主控台樹狀目錄中，以滑鼠右鍵按一下**SampleApplication**，然後按一下**開始**。  
  
8. 在主控台樹狀目錄中，按一下**應用程式**。  
  
9. 在 [應用程式詳細資料] 窗格中，檢查**狀態**的**SampleApplication**會**Started**。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 您設定並啟動 SampleApplication 應用程式  
  
## <a name="next-steps"></a>後續步驟  
 插入新的員工，在測試應用程式**員工**資料表中所述[步驟 4： 測試應用程式](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2： 設定的連接埠](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md)   
 [步驟 4： 測試應用程式](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md)   
 [第 5 課：部署方案](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)