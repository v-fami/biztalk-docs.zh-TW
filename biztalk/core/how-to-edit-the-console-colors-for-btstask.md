---
title: 如何編輯 BTSTask 的主控台色彩 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 725dcb7b-5a19-4166-9d1c-93f30ddca201
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f52c727d2606898084d6397e6eb1b96ddc129b6d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974865"
---
# <a name="how-to-edit-the-console-colors-for-btstask"></a><span data-ttu-id="325d7-102">如何編輯 BTSTask 的主控台色彩</span><span class="sxs-lookup"><span data-stu-id="325d7-102">How to Edit the Console Colors for BTSTask</span></span>
<span data-ttu-id="325d7-103">本主題說明如何編輯 BTSTask 輸出至主控台的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="325d7-103">This topic describes how to edit the foreground colors that BTSTask outputs to the console.</span></span> <span data-ttu-id="325d7-104">如果主控台背景色彩是白色的，就難以判讀 BTSTask 主控台預設輸出，因而需要修改主控台前景色彩。</span><span class="sxs-lookup"><span data-stu-id="325d7-104">If your console background color is white, you will have difficulty reading the default BTSTask console output and will need to modify the console foreground colors.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="325d7-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="325d7-105">Prerequisites</span></span>  
 <span data-ttu-id="325d7-106">若要執行本主題中的程序，您必須對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝資料夾內的 BTSTask.exe.config 檔案具有讀取/寫入權限。</span><span class="sxs-lookup"><span data-stu-id="325d7-106">To perform the procedure in this topic, you must have Read/Write permissions on the BTSTask.exe.config file contained in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder.</span></span>  
  
### <a name="to-edit-the-console-foreground-colors-for-btstask"></a><span data-ttu-id="325d7-107">編輯 BTSTask 的主控台前景色彩</span><span class="sxs-lookup"><span data-stu-id="325d7-107">To edit the console foreground colors for BTSTask</span></span>  
  
1. <span data-ttu-id="325d7-108">在您要執行 BTSTask 的電腦上，使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]、文字編輯器或 XML 編輯器開啟 BTSTask.exe.config。</span><span class="sxs-lookup"><span data-stu-id="325d7-108">On the computer where you want to run BTSTask, open BTSTask.exe.config in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] or a text or XML editor.</span></span> <span data-ttu-id="325d7-109">該檔案位於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝資料夾內。</span><span class="sxs-lookup"><span data-stu-id="325d7-109">This file is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder.</span></span>  
  
2. <span data-ttu-id="325d7-110">編輯 Console.ForegroundColor.Error、 Console.ForegroundColor.Warning 和 Console.ForegroundColor.Info 索引鍵，根據您所需的錯誤訊息、 警告和資訊，請分別的主控台前景色彩的值，然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="325d7-110">Edit the values for the Console.ForegroundColor.Error, Console.ForegroundColor.Warning, and Console.ForegroundColor.Info keys according to the console foreground colors that you want for error messages, warnings, and information, respectively, and then save the file.</span></span> <span data-ttu-id="325d7-111">(如果是單色螢幕，請刪除這三個項目而不要編輯其值)。</span><span class="sxs-lookup"><span data-stu-id="325d7-111">(For monochrome, delete these three entries, rather than editing their values.)</span></span>  
  
    <span data-ttu-id="325d7-112">前景色彩可用的值如下：</span><span class="sxs-lookup"><span data-stu-id="325d7-112">The available values for foreground colors are as follows:</span></span>  
  
    <span data-ttu-id="325d7-113">0： 黑色</span><span class="sxs-lookup"><span data-stu-id="325d7-113">0: Black</span></span>  
  
    <span data-ttu-id="325d7-114">1: DarkBlue</span><span class="sxs-lookup"><span data-stu-id="325d7-114">1: DarkBlue</span></span>  
  
    <span data-ttu-id="325d7-115">2： 深綠</span><span class="sxs-lookup"><span data-stu-id="325d7-115">2: DarkGreen</span></span>  
  
    <span data-ttu-id="325d7-116">3: DarkCyan</span><span class="sxs-lookup"><span data-stu-id="325d7-116">3: DarkCyan</span></span>  
  
    <span data-ttu-id="325d7-117">4: DarkRed</span><span class="sxs-lookup"><span data-stu-id="325d7-117">4: DarkRed</span></span>  
  
    <span data-ttu-id="325d7-118">5: DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="325d7-118">5: DarkMagenta</span></span>  
  
    <span data-ttu-id="325d7-119">6: DarkYellow</span><span class="sxs-lookup"><span data-stu-id="325d7-119">6: DarkYellow</span></span>  
  
    <span data-ttu-id="325d7-120">7： 灰色</span><span class="sxs-lookup"><span data-stu-id="325d7-120">7: Gray</span></span>  
  
    <span data-ttu-id="325d7-121">8： 暗灰色</span><span class="sxs-lookup"><span data-stu-id="325d7-121">8: DarkGray</span></span>  
  
    <span data-ttu-id="325d7-122">9： 藍色</span><span class="sxs-lookup"><span data-stu-id="325d7-122">9: Blue</span></span>  
  
    <span data-ttu-id="325d7-123">10： 綠色</span><span class="sxs-lookup"><span data-stu-id="325d7-123">10: Green</span></span>  
  
    <span data-ttu-id="325d7-124">11： 青色</span><span class="sxs-lookup"><span data-stu-id="325d7-124">11: Cyan</span></span>  
  
    <span data-ttu-id="325d7-125">12： 紅色</span><span class="sxs-lookup"><span data-stu-id="325d7-125">12: Red</span></span>  
  
    <span data-ttu-id="325d7-126">13： 洋紅</span><span class="sxs-lookup"><span data-stu-id="325d7-126">13: Magenta</span></span>  
  
    <span data-ttu-id="325d7-127">14： 黃色</span><span class="sxs-lookup"><span data-stu-id="325d7-127">14: Yellow</span></span>  
  
    <span data-ttu-id="325d7-128">15： 空白</span><span class="sxs-lookup"><span data-stu-id="325d7-128">15: White</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="325d7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="325d7-129">See Also</span></span>  
 [<span data-ttu-id="325d7-130">BTSTask 命令列參考</span><span class="sxs-lookup"><span data-stu-id="325d7-130">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)