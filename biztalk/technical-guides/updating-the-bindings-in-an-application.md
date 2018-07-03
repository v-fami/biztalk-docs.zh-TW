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
# <a name="updating-the-bindings-in-an-application"></a><span data-ttu-id="13576-102">更新應用程式中的繫結</span><span class="sxs-lookup"><span data-stu-id="13576-102">Updating the Bindings in an Application</span></span>
<span data-ttu-id="13576-103">當您在應用程式中更新組件時，其繫結通常都會遭到覆寫，或是組件可能根本不會繫結，進而使您必須手動重新設定繫結。</span><span class="sxs-lookup"><span data-stu-id="13576-103">When you update an assembly in an application, its bindings are often overwritten or else the assembly may not be bound at all, forcing you to manually reconfigure bindings.</span></span> <span data-ttu-id="13576-104">若要避免這個問題，您可以使用繫結檔案更新的組件相同版本或較新版本更新組件。</span><span class="sxs-lookup"><span data-stu-id="13576-104">To avoid this, you can use a binding file to update the same version of the assembly or update an assembly with a newer version.</span></span>  
  
## <a name="updating-the-same-version-of-an-assembly"></a><span data-ttu-id="13576-105">正在更新相同版本的組件</span><span class="sxs-lookup"><span data-stu-id="13576-105">Updating the Same Version of an Assembly</span></span>  
 <span data-ttu-id="13576-106">如果組件具有早期繫結連接埠或動態連接埠，而且您有在 [ BizTalk Server 管理主控台] 中變更連接埠組態，當您以具有相同版本號碼的組件來更新組件時，便會遺失設定。</span><span class="sxs-lookup"><span data-stu-id="13576-106">If the assembly has early bound ports or dynamic ports, and you changed the port configuration in the BizTalk Server Administration console, the settings will be lost when you update the assembly with an assembly having the same version number.</span></span> <span data-ttu-id="13576-107">您可以在您要更新之組件匯出繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="13576-107">You can export a binding file for the assembly that you are going to update.</span></span> <span data-ttu-id="13576-108">在更新組件之後, 可以組件匯入應用程式，然後重新套用先前的繫結其繫結檔案匯入。</span><span class="sxs-lookup"><span data-stu-id="13576-108">After updating the assembly, you can import the assembly into the application and then import its binding file to reapply the previous bindings.</span></span>  
  
## <a name="updating-an-assembly-with-a-newer-version"></a><span data-ttu-id="13576-109">更新較新版本的組件</span><span class="sxs-lookup"><span data-stu-id="13576-109">Updating an Assembly with a Newer Version</span></span>  
 <span data-ttu-id="13576-110">您可以藉由匯出繫結至繫結檔案的單一組件相關聯、 編輯以反映新的組件版本，該繫結檔案，然後匯入的組件繫結到應用程式更新的組件版本。</span><span class="sxs-lookup"><span data-stu-id="13576-110">You can update the version of an assembly by exporting the binding associated with a single assembly into a binding file, editing the binding file to reflect a new assembly version, and then importing the bindings of the assembly into the application.</span></span> <span data-ttu-id="13576-111">如需有關編輯繫結檔案的詳細資訊，請參閱 <<c0> [ 自訂繫結檔案](http://go.microsoft.com/fwlink/?LinkID=155000)(HYPERLINK"<http://go.microsoft.com/fwlink/?LinkID=155000>" <http://go.microsoft.com/fwlink/?LinkID=155000>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="13576-111">For more information about editing a binding file, see [Customizing Binding Files](http://go.microsoft.com/fwlink/?LinkID=155000) ( HYPERLINK "<http://go.microsoft.com/fwlink/?LinkID=155000>" <http://go.microsoft.com/fwlink/?LinkID=155000>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>