---
title: "更新應用程式中的繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe4ee4d8-67bf-4137-94e2-8274107c8ed6
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d4d30296a2bb81b3685793884010f02eb950828
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="updating-the-bindings-in-an-application"></a>更新應用程式中的繫結
當您在應用程式中更新組件時，其繫結通常都會遭到覆寫，或是組件可能根本不會繫結，進而使您必須手動重新設定繫結。 若要避免這個問題，您可以使用繫結檔案更新的組件相同版本或更新組件的較新版本。  
  
## <a name="updating-the-same-version-of-an-assembly"></a>正在更新相同版本的組件  
 如果組件具有早期繫結連接埠或動態連接埠，而且您有在 [ BizTalk Server 管理主控台] 中變更連接埠組態，當您以具有相同版本號碼的組件來更新組件時，便會遺失設定。 您可以為將要更新的組件匯出繫結檔案。 在更新組件之後, 可以組件匯入應用程式，然後重新套用先前的繫結其繫結檔案匯入。  
  
## <a name="updating-an-assembly-with-a-newer-version"></a>更新組件的較新版本  
 您可以匯出到繫結檔案中的單一組件相關聯的繫結、 編輯以反映新的組件版本，該繫結檔案，然後匯入之組件的繫結至應用程式來更新組件的版本。 如需有關編輯繫結檔案的詳細資訊，請參閱[自訂繫結檔案](http://go.microsoft.com/fwlink/?LinkID=155000)(超連結"http://go.microsoft.com/fwlink/?LinkID=155000"http://go.microsoft.com/fwlink/?LinkID=155000) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。