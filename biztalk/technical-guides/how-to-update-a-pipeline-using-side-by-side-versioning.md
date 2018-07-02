---
title: 如何更新管線中使用的並存版本控制 |Microsoft Docs
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
ms.openlocfilehash: 4bf978b64876a91d06acfbe4c5d34278935cfa55
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970887"
---
# <a name="how-to-update-a-pipeline-using-side-by-side-versioning"></a>如何更新管線中使用的並存版本控制
使用新的管線新增--並存版本控制的簡單方式是選取的新部署的管線版本中的傳送埠或接收位置。 這會取代舊的管線，以新的。 不過，如果您需要針對回溯相容性的則為 true 的並排顯示功能，然後您必須建立新傳送埠和接收位置和繫結至指定的新管線版本。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。  
  
### <a name="to-add-a-new-version-of-a-pipeline-component"></a>若要加入新的管線元件的版本  
  
1. 在 Visual Studio 中建立新管線元件的版本，以及簽署組件。  
  
2. 將管線元件中的新增**管線元件**資料夾 (\<*安裝資料夾*\>\Pipeline Components)。  
  
3. 將管線元件新增至您的管線。  
  
4. 建置管線，或部署您的方案之後, 移除管線元件，從**管線元件**資料夾。  
  
5. 將管線元件新增至全域組件快取 (GAC) 中。  
  
   您已完成這些步驟之後，已編譯的管線組件將參考的管線元件的正確版本和 BizTalk Server 所使用的 AppDomain 會發現在 GAC 中，而不是尋找先前的管線元件的新版本管線元件資料夾中的管線元件的版本。  
  
## <a name="see-also"></a>另請參閱  
 [使用並存版本控制進行更新](../technical-guides/updating-using-side-by-side-versioning.md)