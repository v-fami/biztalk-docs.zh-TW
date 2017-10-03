---
title: "如何更新管線中使用的並存版本控制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd884a76-71dd-4c90-b4ba-f1cd7f48eb04
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c4e8803128f2232905229de3b5de49994e039ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-a-pipeline-using-side-by-side-versioning"></a>如何更新管線中使用的並存版本控制
使用新加入的並存版本控制的管線的簡單方式是選取的新部署的管線版本中的傳送埠或接收位置。 這將會以新的取代舊的管線。 不過，如果您需要則為 true 來並行功能的回溯相容性，然後您必須建立新傳送埠和接收位置和繫結至指定的新管線版本。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。  
  
### <a name="to-add-a-new-version-of-a-pipeline-component"></a>若要新增管線元件的版本  
  
1.  在 Visual Studio 中，建立新版本的管線元件，並簽署組件。  
  
2.  新增管線元件中的**管線元件**資料夾 (\<*安裝資料夾*> \Pipeline Components)。  
  
3.  將管線元件加入至您的管線。  
  
4.  建立管線，或部署方案之後, 移除管線元件從**管線元件**資料夾。  
  
5.  將管線元件加入至全域組件快取 (GAC)。  
  
 您已經完成這些步驟後，在已編譯的管線組件將參考的管線元件的正確版本所使用的 AppDomain[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]將在 GAC 中，尋找新版本的管線元件，而不是尋找上一個管線元件資料夾中的管線元件的版本。  
  
## <a name="see-also"></a>另請參閱  
 [更新使用-並存版本控制](../technical-guides/updating-using-side-by-side-versioning.md)