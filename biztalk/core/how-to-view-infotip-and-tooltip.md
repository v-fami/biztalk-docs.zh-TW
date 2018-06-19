---
title: 如何檢視資訊提示和工具提示 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5621bd0a-7028-43fc-b6e8-74a528129285
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06aba645f94b87e0a7951d9c8264056262a12a13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257278"
---
# <a name="how-to-view-infotip-and-tooltip"></a>如何檢視資訊提示與工具提示
當您將游標移至對應項目上方而不選取它時，會顯示含有該項目之實用資訊的工具提示。  
  
 BizTalk 對應工具使用兩種類型的工具提示 – 資訊提示和工具提示。  
  
-   **資訊提示**會顯示運算質或連結。 當您為運算質或連結設定標籤或註解時，會在格線頁上以資訊提示的形式看見它們。 此外，當屬性的文字值超過顯示**屬性方格**，資訊提示會顯示。  
  
-   **工具提示**部分/整個隱藏的資料格檢視中目前的對齊方式的結構描述節點會顯示。  
  
 對於連結標籤，只會保留前 256 個字元，而工具提示會顯示完整的標籤。 對於運算質，標籤最多可包含 256 個字元，而註解則有 1024 個字元的限制。 註解的文字會因此而截斷，以便只顯示註解的前 256 個字元。  
  
## <a name="prerequisites"></a>必要條件  
 如果要檢視工具提示，請確定 BizTalk 對應工具正在執行。  
  
## <a name="to-view-the-infotip"></a>檢視資訊提示  
 當您將滑鼠游標移至運算質上方時，資訊提示會顯示關於運算質名稱、運算質標籤、運算質註解與輸入參數 (如果有的話) 的資訊。 如**指令碼處理**運算質，資訊提示會顯示第一個幾行程式碼。  
  
 連結的資訊提示會顯示下列資訊：  
  
-   連結標籤 (如果已設定的話)。  
  
-   **： 從來源連接**。 如果來源連接是結構描述項目，會顯示項目名稱。 如果來源連接是運算質，會顯示運算質名稱。  
  
-   **至： 目的地連接**。 如果目的地連接是結構描述項目，會顯示項目名稱。 如果目的地連接是運算質，會顯示運算質名稱。  
  
 如果中的欄位**屬性方格**文字超過顯示，將滑鼠游標移欄位。 資訊提示就會顯示完整文字。  
  
 下圖說明與運算質，資訊提示的連結，而**屬性方格**。  
  
 ![運算質、 連結及標籤的資訊提示](../core/media/viewing-infotips.gif "Viewing_infotips")  
  
## <a name="to-view-the-tooltip"></a>檢視工具提示  
 當您的來源和/或目的地結構描述過大時，您的對應可能會過長，因此可能只看得到部分結構描述節點。 在此狀況下，當您將滑鼠游標移至那些來源節點上方時，就可以看到工具提示。  
  
 下圖顯示某個部分隱藏之目標結構描述節點的工具提示。  
  
 ![結構描述節點的工具提示](../core/media/viewing-tooltips.gif "Viewing_tooltips")  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 對應工具](../core/using-biztalk-mapper.md)