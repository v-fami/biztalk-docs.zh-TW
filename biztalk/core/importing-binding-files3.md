---
title: "匯入繫結 Files3 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- target computer, cleaning
- importing binding files
- cleaning target computer
ms.assetid: 955bb3e1-3dbc-43ce-9126-205d838ae662
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa1d95c40e3e556068e15a269ee4cbb7e995429a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-binding-files"></a>匯入繫結檔案
使用 BizTalk Server 匯入繫結檔案之前，請確認下列項目：  
  
-   CLASSPATH 指向 JD Edwards 專屬檔案的特定位置。 確認這些檔案的位置在新電腦上是相同的，否則請編輯繫結檔案。  
  
-   在新電腦上用於存放回應的資料夾存在且相同，否則請編輯繫結檔案。  
  
-   JD Edwards 系統密碼 (如果出現在組態中) 會以 ***** 格式儲存在繫結檔案中。 如需詳細資訊，請參閱[部署限制](../core/deployment-limitations2.md)。  
  
> [!NOTE]
>  部署會覆寫接收位置組態。 在目標電腦上部署繫結檔案 (和組件) 時，傳送埠和接收位置會在匯入時被取代為 XML 繫結檔案中的傳送埠和接收位置。  
  
## <a name="importing-the-binding-files"></a>匯入繫結檔案  
 您可以使用下列程序，匯入繫結檔案。  
  
#### <a name="to-import-the-binding-files"></a>若要匯入繫結檔案  
  
1.  上**啟動**功能表上，指向**Program Files**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**啟動 BizTalk Server 管理主控台。  
  
2.  依序展開 BizTalk Server 管理**BizTalk 群組**，然後展開**應用程式**。  
  
3.  以滑鼠右鍵按一下所需的應用程式，指向**匯入**，然後按一下 **繫結**。  
  
4.  在**匯入繫結**對話方塊中，瀏覽並選取繫結檔案，然後按一下**開啟**。  
  
## <a name="cleaning-the-target-computer"></a>清除目標電腦  
 使用下列程序來清除目標電腦。  
  
#### <a name="to-clean-the-target-computer"></a>若要清除目標電腦  
  
-   移除傳送埠和接收位置繫結至協調流程。  
  
## <a name="see-also"></a>另請參閱  
 [建立 JD Edwards OneWorld 傳送處理常式](../core/creating-jd-edwards-oneworld-send-handlers.md)   
 [部署連接埠和組件](../core/deploying-ports-and-assemblies4.md)