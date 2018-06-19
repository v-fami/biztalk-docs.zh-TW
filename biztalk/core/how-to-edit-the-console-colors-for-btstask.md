---
title: 如何編輯 BTSTask 的主控台色彩 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 725dcb7b-5a19-4166-9d1c-93f30ddca201
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d68529f01ab8131739d735ad82d804b41a9c021
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254038"
---
# <a name="how-to-edit-the-console-colors-for-btstask"></a>如何編輯 BTSTask 的主控台色彩
本主題說明如何編輯 BTSTask 輸出至主控台的前景色彩。 如果主控台背景色彩是白色的，就難以判讀 BTSTask 主控台預設輸出，因而需要修改主控台前景色彩。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝資料夾內的 BTSTask.exe.config 檔案具有讀取/寫入權限。  
  
### <a name="to-edit-the-console-foreground-colors-for-btstask"></a>編輯 BTSTask 的主控台前景色彩  
  
1.  在您要執行 BTSTask 的電腦上，使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]、文字編輯器或 XML 編輯器開啟 BTSTask.exe.config。 該檔案位於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝資料夾內。  
  
2.  編輯 Console.ForegroundColor.Error、 Console.ForegroundColor.Warning 和 Console.ForegroundColor.Info 機碼，根據您想要用於錯誤訊息、 警告和資訊，請分別的主控台前景色彩的值，然後儲存檔案。 (如果是單色螢幕，請刪除這三個項目而不要編輯其值)。  
  
     前景色彩可用的值如下：  
  
     0： 黑色  
  
     1: DarkBlue  
  
     2: DarkGreen  
  
     3: DarkCyan  
  
     4: DarkRed  
  
     5: DarkMagenta  
  
     6: DarkYellow  
  
     7： 灰色  
  
     8： 暗灰色  
  
     9： 藍色  
  
     10： 綠色  
  
     11： 青色  
  
     12： 紅色  
  
     13： 洋紅  
  
     14： 黃色  
  
     15： 空白  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)