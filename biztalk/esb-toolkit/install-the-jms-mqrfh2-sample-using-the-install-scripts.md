---
title: "使用安裝指令碼的 JMS MQRFH2 範例安裝 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 785f3e32-83b4-406a-af1b-9499115fbb8f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edb3102fabc84818cb42fcdcba6a034d085bdcc4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="install-the-jms-mqrfh2-sample-using-the-install-scripts"></a>安裝 JMS MQRFH2 範例使用安裝指令碼
本章節描述如何安裝使用所提供的安裝指令碼的 JMS MQRFH2 範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。  
  
 **若要安裝 JMS MQRFH2 範例的安裝指令碼**  
  
1.  使用 WebSphere 總管 中，建立具有名稱的佇列管理員**ESB。JMS。Sample.QueueManager**。  
  
2.  使用 WebSphere 總管 中，建立下列四個佇列內**ESB。JMS。Sample.QueueManager:**  
  
    -   ESB。JMS。範例。DYNAMICQ1  
  
    -   ESB。JMS。範例。DYNAMICQ2  
  
    -   ESB。JMS。範例。回覆  
  
    -   ESB。JMS。範例。SENDTOBIZTALK  
  
3.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
4.  在**執行** 對話方塊中，輸入**cmd**，然後按 ENTER 鍵。  
  
5.  執行下列命令，取代*\<路徑\>*參數與您想要安裝的.cmd 檔案的完整路徑 (在此版本中的預設路徑是 \Source\Samples\JMS\Install\Scripts\\):  
  
    ```  
    <path>\Setup_bin.cmd  
    ```