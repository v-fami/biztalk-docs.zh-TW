---
title: 模組 7： 測試有效一般檔案執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing, flat file instance
- tutorial, testing flat file instance
- flat files, testing
ms.assetid: ba8a5d81-41b0-4da7-8c2e-02cf29953af7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2344e537fe2b66720e0df9296e22145d1c23bfa6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972247"
---
# <a name="module-7-testing-a-valid-flat-file-instance"></a><span data-ttu-id="92b65-102">模組 7： 測試有效一般檔案執行個體</span><span class="sxs-lookup"><span data-stu-id="92b65-102">Module 7: Testing a Valid Flat File Instance</span></span>
<span data-ttu-id="92b65-103">在這個模組中，您可以提交有效的範例檔案的一般檔案接收在前一個實驗室中建立的連接埠的 MT103。</span><span class="sxs-lookup"><span data-stu-id="92b65-103">In this module, you submit a valid sample MT103 flat file to the file receive ports created in the previous labs.</span></span> <span data-ttu-id="92b65-104">這項工作中測試您在上一個實驗室中建立的接收管線。</span><span class="sxs-lookup"><span data-stu-id="92b65-104">This task tests the receive pipelines you created in previous labs.</span></span> <span data-ttu-id="92b65-105">Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]輸出 XML 格式寫入您在上一課中，選取傳送埠的輸出資料夾[第 2 課： 新增 XML 傳送埠](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="92b65-105">Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] writes the output in XML format to the output folder in the send port you selected in the previous lesson, [Lesson 2: Adding an XML Send Port](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md).</span></span>  
  
 <span data-ttu-id="92b65-106">起始檔案接收配接器藉由將 SWIFT 一般格式的檔案複製到輸入資料夾。</span><span class="sxs-lookup"><span data-stu-id="92b65-106">You initiate the file receive adapter by copying a SWIFT flat-formatted file to the inbound folder.</span></span> <span data-ttu-id="92b65-107">此動作會導致[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]路由是有效的 SWIFT XML 檔案傳送至輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="92b65-107">This action results in [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] routing a valid SWIFT XML file to the outbound folder.</span></span>  
  
 <span data-ttu-id="92b65-108">在這個工作中，您也會提交無效的 MT103 訊息。</span><span class="sxs-lookup"><span data-stu-id="92b65-108">In this task, you also submit an MT103 message that is not valid.</span></span> <span data-ttu-id="92b65-109">您可以使用事件來解決這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="92b65-109">You use the Event to resolve the error.</span></span>  
  
 <span data-ttu-id="92b65-110">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="92b65-110">This section contains:</span></span>  
  
-   [<span data-ttu-id="92b65-111">課程 1：提交範例一般檔案</span><span class="sxs-lookup"><span data-stu-id="92b65-111">Lesson 1: Submitting a Sample Flat File</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-1-submitting-a-sample-flat-file.md)  
  
-   [<span data-ttu-id="92b65-112">課程 2：提交無效的 MT103 訊息</span><span class="sxs-lookup"><span data-stu-id="92b65-112">Lesson 2: Submitting an MT103 Message That Is Not Valid</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-2-submitting-an-mt103-message-that-is-not-valid.md)  
  
-   [<span data-ttu-id="92b65-113">課程 3：測試 XML 執行個體</span><span class="sxs-lookup"><span data-stu-id="92b65-113">Lesson 3: Testing an XML Instance</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-3-testing-an-xml-instance.md)