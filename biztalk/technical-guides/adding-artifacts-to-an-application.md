---
title: 將成品新增至應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9b5e92e-2e55-41d7-9959-f62753bbeb04
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c08fa95dddad06efb2c51d93df56b757ae4caca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295646"
---
# <a name="adding-artifacts-to-an-application"></a>將成品新增至應用程式
您可以加入和設定成品，例如傳送和接收埠、 接收位置和協調流程，使用 [管理] 主控台。 您也可以產生繫結檔案，並將它們加入至應用程式中，如果您想要套用不同的繫結的不同的環境，您將匯入到應用程式。  
  
 您可以加入其他 (通常非 BizTalk Server) 成品，例如指令碼、 憑證和讀我檔案的檔案，以在 [資源] 節點下的應用程式。 若要這樣做，請使用管理主控台或 BTSTask。  
  
 如需成品的詳細資訊，請參閱[如何建立或新增成品](http://go.microsoft.com/fwlink/?LinkID=154724)(http://go.microsoft.com/fwlink/?LinkID = 154724)，[管理成品](http://go.microsoft.com/fwlink/?LinkID=154725)(http://go.microsoft.com/fwlink/?LinkID = 154725) 和[繫結檔案和應用程式部署](http://go.microsoft.com/fwlink/?LinkID=154726)(http://go.microsoft.com/fwlink/?LinkID = 154726)。  
  
## <a name="factoring-artifacts-into-multiple-biztalk-applications"></a>成品分解成多個 BizTalk 應用程式  
 在開發過程中，為了方便起見，您可能已經將組件部署到單一應用程式。 您可能會為了各種理由，而想要將成品分解到多個應用程式中，然後再部署到實際執行環境。  
  
 在部署之前，您應該執行深入分析的組件的建構。 判斷是否應該執行任何建構、 完整的建構或最佳的建構。  
  
 **沒有建構**  
  
 所有的 BizTalk 成品是在一個組件。 這是容易了解和部署，但可提供最大的彈性。  
  
 **完整的建構**  
  
 每個 BizTalk 成品是在它自己組件中。 這會提供最大的彈性，但最為複雜部署並了解。  
  
 **最佳建構**  
  
 最佳建構介於無分解和完整的建構基礎 BizTalk 應用程式的深入分析。 除了版本控制，這可讓您更輕鬆地實作您的 BizTalk 主控件設計。 藉由尋找 BizTalk 成品之間的關聯性來達到此目的。 可能的話，請將一律具有版本設定一起在相同的組件中的成品。 如果需要之成品的獨立版本設定，然後將它們必須放在不同的組件中。 這是您想要達到的分解層級。