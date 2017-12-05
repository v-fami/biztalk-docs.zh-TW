---
title: "使用安裝指令碼動態解析範例安裝 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 644b6403-9883-4256-80d5-37881a87ed0e
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 872bb73b9060e25986876c1c2da71afae84b5c52
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="install-the-dynamic-resolution-sample-using-the-install-scripts"></a>安裝使用安裝指令碼動態解析範例
本章節描述如何安裝動態解析 」 範例隨附的安裝指令碼從[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。  
  
 **若要安裝的安裝指令碼動態解析範例**  
  
1.  如果您想要執行使用 FTP 的單向傳訊範例，請建立下列 FTP 站台：  
  
    -   FTP 虛擬目錄名稱： Out  
  
    -   位置： \Source\Samples\DynamicResolution\Test\FTP\Out  
  
    -   權限： 讀取和寫入  
  
    -   確定 BizTalk 應用程式使用者群組具有這個位置的完整存取權限  
  
2.  如果您想要執行使用 MQSeries 的雙向傳訊範例，請建立下列使用 WebSphere Explorer:  
  
    -   具有名稱 ESB 佇列管理員。DEP 來管理。Sample.QueueManager  
  
    -   名為測試佇列。OUT ESB 內。DEP 來管理。Sample.QueueManager  
  
3.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
4.  在**執行** 對話方塊中，輸入**cmd**，然後按 ENTER 開啟命令提示字元。  
  
5.  執行下列命令，取代\<路徑\>參數與您想要安裝的.cmd 檔案的完整路徑 (在此版本中的預設路徑是 \Source\Samples\DynamicResolution\Install\Scripts\\):  
  
    ```  
    <path>\Setup_bin.cmd  
    ```