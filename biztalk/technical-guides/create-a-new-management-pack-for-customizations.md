---
title: 建立用於自訂的新管理組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ce1ffa0-57c7-41ce-b459-48c36522889e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d04b29cd96a66057d83b5212472f0ea69150f0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297590"
---
# <a name="create-a-new-management-pack-for-customizations"></a><span data-ttu-id="8e79e-102">建立用於自訂的新管理組件</span><span class="sxs-lookup"><span data-stu-id="8e79e-102">Create a New Management Pack for Customizations</span></span>
<span data-ttu-id="8e79e-103">大部分的廠商管理組件是密封格式，因此您無法變更任何管理組件檔案中的原始設定。</span><span class="sxs-lookup"><span data-stu-id="8e79e-103">Most vendor management packs are sealed so that you cannot change any of the original settings in the management pack file.</span></span> <span data-ttu-id="8e79e-104">不過，您可以建立自訂，例如覆寫或新的監視物件，並將它們儲存至不同的管理組件。</span><span class="sxs-lookup"><span data-stu-id="8e79e-104">However, you can create customizations, such as overrides or new monitoring objects, and save them to a different management pack.</span></span> <span data-ttu-id="8e79e-105">根據預設，Operations Manager 2007 R2/2012年會將所有自訂都儲存至預設管理組件。</span><span class="sxs-lookup"><span data-stu-id="8e79e-105">By default, Operations Manager 2007 R2/2012 saves all customizations to the Default Management Pack.</span></span> <span data-ttu-id="8e79e-106">最佳做法，您應該改為建立您想要自訂每個密封的管理組件的個別管理組件。</span><span class="sxs-lookup"><span data-stu-id="8e79e-106">As a best practice, you should instead create a separate management pack for each sealed management pack that you want to customize.</span></span>  
  
 <span data-ttu-id="8e79e-107">建立新的管理組件以儲存覆寫有下列好處：</span><span class="sxs-lookup"><span data-stu-id="8e79e-107">Creating a new management pack for storing overrides has the following advantages:</span></span>  
  
-   <span data-ttu-id="8e79e-108">簡化將測試環境和預先生產環境中所建立的自訂匯出至生產環境的程序。</span><span class="sxs-lookup"><span data-stu-id="8e79e-108">It simplifies the process of exporting customizations that were created in your test and pre-production environments to your production environment.</span></span> <span data-ttu-id="8e79e-109">例如，而不要匯出包含來自多個管理組件的預設管理組件，您可以匯出只包含單一管理組件的自訂管理組件。</span><span class="sxs-lookup"><span data-stu-id="8e79e-109">For example, instead of exporting the Default Management Pack that contains customizations from multiple management packs, you can export just the management pack that contains customizations of a single management pack.</span></span>  
  
-   <span data-ttu-id="8e79e-110">您可以刪除原始管理組件，而不需要先刪除預設管理組件。</span><span class="sxs-lookup"><span data-stu-id="8e79e-110">You can delete the original management pack without first having to delete the Default Management Pack.</span></span> <span data-ttu-id="8e79e-111">包含自訂的管理組件取決於原始管理組件。</span><span class="sxs-lookup"><span data-stu-id="8e79e-111">A management pack that contains customizations depends on the original management pack.</span></span> <span data-ttu-id="8e79e-112">此相依性需要先刪除含自訂的管理組件，才能刪除原始管理組件。</span><span class="sxs-lookup"><span data-stu-id="8e79e-112">This dependency requires you to delete the management pack with customizations before you can delete the original management pack.</span></span> <span data-ttu-id="8e79e-113">如果所有自訂都儲存至預設管理組件，您必須先刪除預設管理組件，才能刪除原始管理組件。</span><span class="sxs-lookup"><span data-stu-id="8e79e-113">If all of your customizations are saved to the Default Management Pack, you must delete the Default Management Pack before you can delete an original management pack.</span></span>  
  
-   <span data-ttu-id="8e79e-114">更容易追蹤及更新個別管理組件的自訂。</span><span class="sxs-lookup"><span data-stu-id="8e79e-114">It is easier to track and update customizations to individual management packs.</span></span>  
  
 <span data-ttu-id="8e79e-115">如需詳細資訊大約密封和未密封管理組件，請參閱[管理組件格式](http://go.microsoft.com/fwlink/?LinkID=198193)(http://go.microsoft.com/fwlink/?LinkId=198193)。</span><span class="sxs-lookup"><span data-stu-id="8e79e-115">For more information about sealed and unsealed management packs, see [Management Pack Formats](http://go.microsoft.com/fwlink/?LinkID=198193) (http://go.microsoft.com/fwlink/?LinkId=198193).</span></span> <span data-ttu-id="8e79e-116">如需管理組件自訂的詳細資訊，請參閱[自訂管理組件](http://go.microsoft.com/fwlink/?LinkID=198194)(http://go.microsoft.com/fwlink/?LinkID=198194)。</span><span class="sxs-lookup"><span data-stu-id="8e79e-116">For more information about management pack customizations, see [Customizing Management Packs](http://go.microsoft.com/fwlink/?LinkID=198194) (http://go.microsoft.com/fwlink/?LinkID=198194).</span></span>