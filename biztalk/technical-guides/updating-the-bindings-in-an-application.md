---
title: 更新應用程式中的繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe4ee4d8-67bf-4137-94e2-8274107c8ed6
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0add0638196e992f74ab53ebda7c429c97ca3aab
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996559"
---
# <a name="updating-the-bindings-in-an-application"></a>更新應用程式中的繫結
當您在應用程式中更新組件時，其繫結通常都會遭到覆寫，或是組件可能根本不會繫結，進而使您必須手動重新設定繫結。 若要避免這個問題，您可以使用繫結檔案更新的組件相同版本或較新版本更新組件。  
  
## <a name="updating-the-same-version-of-an-assembly"></a>正在更新相同版本的組件  
 如果組件具有早期繫結連接埠或動態連接埠，而且您有在 [ BizTalk Server 管理主控台] 中變更連接埠組態，當您以具有相同版本號碼的組件來更新組件時，便會遺失設定。 您可以在您要更新之組件匯出繫結檔案。 在更新組件之後, 可以組件匯入應用程式，然後重新套用先前的繫結其繫結檔案匯入。  
  
## <a name="updating-an-assembly-with-a-newer-version"></a>更新較新版本的組件  
 您可以藉由匯出繫結至繫結檔案的單一組件相關聯、 編輯以反映新的組件版本，該繫結檔案，然後匯入的組件繫結到應用程式更新的組件版本。 如需有關編輯繫結檔案的詳細資訊，請參閱 <<c0> [ 自訂繫結檔案](http://go.microsoft.com/fwlink/?LinkID=155000)(HYPERLINK"<http://go.microsoft.com/fwlink/?LinkID=155000>" <http://go.microsoft.com/fwlink/?LinkID=155000>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。