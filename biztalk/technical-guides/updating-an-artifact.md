---
title: 更新成品 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 40feab57-4286-4bdf-8f52-25d02b3fa60c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17d5f2ad910c59ded9c2499c929d73480fac7b51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302574"
---
# <a name="updating-an-artifact"></a>更新成品
兩個或多個 BizTalk 應用程式中成品之間的相依性可以有大幅影響應用程式部署和維護。 成品相依於另一個需要使用該成品才能正常運作時，例如協調流程，需要使用特定的管線才能正確傳輸訊息。  
  
 若要更新應用程式中的成品，您必須先解除部署，以及相依於它的任何成品。 當具有相依性的成品存在於相同的應用程式中時，BizTalk Server 會自動針對更新和相依的成品處理解除部署和重新部署工作。 但是，當具有相依性的成品存在於其他應用程式中時，就不是這個情況。 如果您想要更新一個的應用程式中的成品上的另一個應用程式中的成品有相依性，您必須解除部署，並重新部署相依的成品以手動方式，如下所示：  
  
1.  停止、取消登錄和解除繫結此相依成品。  
  
2.  更新它所相依的成品。  
  
3.  繫結、登錄和啟動此相依成品。  
  
 若要避免需要執行手動步驟來更新其他成品所相依，您可以嘗試將具有相依性的所有成品一起都保留相同的應用程式。 這不一定可行的不過，因為大多數類型的成品必須是唯一的 BizTalk 群組中。 您不能在相同群組的兩個不同應用程式中有相同的成品，即使當這兩個應用程式包含的成品相依於相同的成品時，也是如此。 唯一的成品的問題有關的詳細資訊，請參閱[成品，必須是唯一的應用程式或群組](http://go.microsoft.com/fwlink/?LinkId=155141)(http://go.microsoft.com/fwlink/?LinkId=155141) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
 您可以將所需的成品加入至一個應用程式，然後再加入至該應用程式從任何其他成品，相依於它的應用程式的參考。 當您加入應用程式的參考時，該應用程式中的成品可以使用它所參考之應用程式中的任何成品。 如需新增參考的指示，請參閱[如何加入另一個應用程式的參考](http://go.microsoft.com/fwlink/?LinkID=155011)(http://go.microsoft.com/fwlink/?LinkID=155011) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
 更新成品在 BizTalk 應用程式中工作的檢查清單，請參閱[檢查清單： 更新 BizTalk 應用程式中的成品](http://go.microsoft.com/fwlink/?LinkId=155647)(http://go.microsoft.com/fwlink/?LinkId=155647) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
## <a name="see-also"></a>另請參閱  
 [更新應用程式和成品](../technical-guides/updating-applications-and-artifacts.md)