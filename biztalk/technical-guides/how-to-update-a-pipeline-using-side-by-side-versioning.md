---
title: 如何更新管線中使用的並存版本控制 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd884a76-71dd-4c90-b4ba-f1cd7f48eb04
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a5b977d8f0d1964df33c2b2f549bd420d0d3179
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008375"
---
# <a name="how-to-update-a-pipeline-using-side-by-side-versioning"></a>如何更新管線中使用的並存版本控制
使用新加入的並存版本控制的管線的簡單方式是選取的新部署的管線版本中的傳送埠或接收位置。 這將會以新的取代舊的管線。 不過，如果您需要則為 true 來並行功能的回溯相容性，然後您必須建立新傳送埠和接收位置和繫結至指定的新管線版本。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。  
  
### <a name="to-add-a-new-version-of-a-pipeline-component"></a>若要新增管線元件的版本  
  
1.  在 Visual Studio 中，建立新版本的管線元件，並簽署組件。  
  
2.  新增管線元件中的**管線元件**資料夾 (\<*安裝資料夾*\>\Pipeline Components)。  
  
3.  將管線元件加入至您的管線。  
  
4.  建立管線，或部署方案之後, 移除管線元件從**管線元件**資料夾。  
  
5.  將管線元件加入至全域組件快取 (GAC)。  
  
 完成這些步驟之後，管線已編譯的組件將參考的管線元件的正確版本，而 BizTalk Server 所使用的 AppDomain 會發現在 GAC 中，而不是尋找先前的管線元件的新版本管線元件資料夾中的管線元件的版本。  
  
## <a name="see-also"></a>請參閱  
 [使用並存版本控制進行更新](../technical-guides/updating-using-side-by-side-versioning.md)