---
title: "第 3 課： 測試 XML 執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, XML instances
- XML instances
ms.assetid: 19d7dd18-17dc-4355-a4f1-5c5e6750faf3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 948ea484b5cc3138a73a67b384705ed73d9478b2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="lesson-3-testing-an-xml-instance"></a><span data-ttu-id="c5221-102">第 3 課： 測試 XML 執行個體</span><span class="sxs-lookup"><span data-stu-id="c5221-102">Lesson 3: Testing an XML Instance</span></span>
<span data-ttu-id="c5221-103">在這一課，您可以提交有效 MT103，XML 格式檔案中的訊息接收在先前課程所建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c5221-103">In this lesson, you submit a valid MT103 message in XML format to the file receive ports created in the previous lessons.</span></span> <span data-ttu-id="c5221-104">這個動作會測試您在前一個模組中建立的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="c5221-104">This action tests the send pipelines that you created in previous modules.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="c5221-105">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]以一般檔案中將輸出寫入您選取的前一個模組中的傳送埠的輸出資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c5221-105">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] writes the output as a flat file to the output folder that you selected for the send port in the previous module.</span></span>  
  
 <span data-ttu-id="c5221-106">起始檔案接收配接器複製到輸入資料夾的 SWIFT XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="c5221-106">You initiate the file receive adapter by copying a SWIFT XML-formatted file to the inbound folder.</span></span> <span data-ttu-id="c5221-107">這個動作會導致系統複製到輸出資料夾的有效 SWIFT 一般檔案。</span><span class="sxs-lookup"><span data-stu-id="c5221-107">This action results in the system copying a valid SWIFT flat file to the outbound folder.</span></span>  
  
### <a name="to-test-an-xml-instance"></a><span data-ttu-id="c5221-108">若要測試 XML 執行個體</span><span class="sxs-lookup"><span data-stu-id="c5221-108">To test an XML Instance</span></span>  
  
1.  <span data-ttu-id="c5221-109">在 Windows 檔案總管 中，開啟\<*磁碟機*\>: \Labs\Outbound。</span><span class="sxs-lookup"><span data-stu-id="c5221-109">In Windows Explorer, open \<*drive*\>:\Labs\Outbound.</span></span> <span data-ttu-id="c5221-110">請確認此資料夾包含您傳送至這個資料夾中的 {GUID}.xml 檔案[第 1 課： 送出範例一般檔案](../../adapters-and-accelerators/accelerator-swift/lesson-1-submitting-a-sample-flat-file.md)此模組。</span><span class="sxs-lookup"><span data-stu-id="c5221-110">Verify that this folder contains the {GUID}.xml file that you sent to this folder in [Lesson 1: Submitting a Sample Flat File](../../adapters-and-accelerators/accelerator-swift/lesson-1-submitting-a-sample-flat-file.md) of this module.</span></span>  
  
2.  <span data-ttu-id="c5221-111">複製 XML 檔案，並將它貼入\<*磁碟機*\>: \Labs\Inbound\XMLFile。</span><span class="sxs-lookup"><span data-stu-id="c5221-111">Copy the XML file, and paste it into \<*drive*\>:\Labs\Inbound\XMLFile.</span></span> <span data-ttu-id="c5221-112">請注意，您所貼上這個檔案的時間。</span><span class="sxs-lookup"><span data-stu-id="c5221-112">Note the time that you pasted this file.</span></span>  
  
3.  <span data-ttu-id="c5221-113">移至\<*磁碟機*\>: \Labs\Outbound。</span><span class="sxs-lookup"><span data-stu-id="c5221-113">Move to \<*drive*\>:\Labs\Outbound.</span></span> <span data-ttu-id="c5221-114">請確認沒有在這個資料夾中，稱為 {GUID}.txt 的檔案，而且這個檔案修改日期資料行中的時間，對應至您所貼上檔案的時間\<*磁碟機*\>: \Labs\Inbound\XMLFile。</span><span class="sxs-lookup"><span data-stu-id="c5221-114">Verify that there is a file called {GUID}.txt in this folder, and that the time in the Date Modified column for this file corresponds to the time that you pasted the file into \<*drive*\>:\Labs\Inbound\XMLFile.</span></span>  
  
4.  <span data-ttu-id="c5221-115">在 [記事本] 開啟中的 MT103_Sample.txt \<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial。</span><span class="sxs-lookup"><span data-stu-id="c5221-115">In Notepad, open MT103_Sample.txt in \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial.</span></span>  
  
5.  <span data-ttu-id="c5221-116">在 記事本 的另一個執行個體，開啟 {GUID} 中的.txt \<*磁碟機*\>: \Labs\Inbound\XMLFile。</span><span class="sxs-lookup"><span data-stu-id="c5221-116">In another instance of Notepad, open {GUID}.txt in \<*drive*\>:\Labs\Inbound\XMLFile.</span></span>  
  
6.  <span data-ttu-id="c5221-117">請確認 [記事本] 中的兩個檔案都包含相同的內容。</span><span class="sxs-lookup"><span data-stu-id="c5221-117">Verify that the two files in Notepad contain the same content.</span></span>  
  
 <span data-ttu-id="c5221-118">若要繼續[單元 8： 修復無效的訊息](http://msdn.microsoft.com/en-us/fb531b22-ac7a-4620-b395-87aebf56077d)。</span><span class="sxs-lookup"><span data-stu-id="c5221-118">Proceed to [Module 8: Repairing an Invalid Message](http://msdn.microsoft.com/en-us/fb531b22-ac7a-4620-b395-87aebf56077d).</span></span>