---
title: File 配接器屬性結構描述和屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [File adapters], properties
- schemas, File adapters
- File adapters, schemas
- Password property [File adapters]
- ReceivedFileName property [File adapters]
- configuring [File adapters], schemas
- CopyMode property [File adapters]
- AllowCacheOnWrite property [File adapters]
- FileCreationTime property [File adapters]
- UserName property, File adapters
- File adapters, properties
- UserName property
ms.assetid: c5ae5339-67bf-4fde-a721-5b1aa3b9caca
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37e1c6860b002b41555337a0bf7e8cb931f2c2bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245990"
---
# <a name="file-adapter-property-schema-and-properties"></a><span data-ttu-id="2bb53-102">File 配接器屬性結構描述和屬性</span><span class="sxs-lookup"><span data-stu-id="2bb53-102">File adapter property schema and properties</span></span>
<span data-ttu-id="2bb53-103">下表包含 FILE 配接器屬性結構描述中的屬性。</span><span class="sxs-lookup"><span data-stu-id="2bb53-103">The following table contains the properties in the File adapter property schema.</span></span>  
  
 <span data-ttu-id="2bb53-104">**命名空間：** http://schemas.microsoft.com/BizTalk/2003/file-properties</span><span class="sxs-lookup"><span data-stu-id="2bb53-104">**Namespace:** http://schemas.microsoft.com/BizTalk/2003/file-properties</span></span>  
  
|<span data-ttu-id="2bb53-105">名稱</span><span class="sxs-lookup"><span data-stu-id="2bb53-105">Name</span></span>|<span data-ttu-id="2bb53-106">型別</span><span class="sxs-lookup"><span data-stu-id="2bb53-106">Type</span></span>|<span data-ttu-id="2bb53-107">Description</span><span class="sxs-lookup"><span data-stu-id="2bb53-107">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="2bb53-108">**CopyMode**</span><span class="sxs-lookup"><span data-stu-id="2bb53-108">**CopyMode**</span></span>|<span data-ttu-id="2bb53-109">xs:unsignedInt</span><span class="sxs-lookup"><span data-stu-id="2bb53-109">xs:unsignedInt</span></span>|<span data-ttu-id="2bb53-110">定義將訊息寫入檔案時使用的複製模式。</span><span class="sxs-lookup"><span data-stu-id="2bb53-110">Defines the copy mode to use when writing a message to a file.</span></span> <span data-ttu-id="2bb53-111">有效值為：</span><span class="sxs-lookup"><span data-stu-id="2bb53-111">Valid values are:</span></span><br /><br /> <span data-ttu-id="2bb53-112">**附加 (0)。**</span><span class="sxs-lookup"><span data-stu-id="2bb53-112">**Append (0).**</span></span> <span data-ttu-id="2bb53-113">若檔案存在，FILE 傳送處理常式會開啟檔案，並將訊息附加到檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="2bb53-113">The File send handler opens a file if it exists and appends a message to the end of the file.</span></span> <span data-ttu-id="2bb53-114">若檔案不存在，FILE 傳送處理常式會建立新檔案。</span><span class="sxs-lookup"><span data-stu-id="2bb53-114">If the file does not exist, the File send handler creates a new file.</span></span><br /><br /> <span data-ttu-id="2bb53-115">**建立新的 (1)。**</span><span class="sxs-lookup"><span data-stu-id="2bb53-115">**Create new (1).**</span></span> <span data-ttu-id="2bb53-116">若檔案不存在，FILE 傳送處理常式會建立新檔案並寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="2bb53-116">If a file does not exist, the File send handler creates a new file and writes to it.</span></span> <span data-ttu-id="2bb53-117">若檔案已存在，FILE 傳送處理常式會報告錯誤，然後依照傳送埠的一般配接器重試邏輯來處理。</span><span class="sxs-lookup"><span data-stu-id="2bb53-117">If the file already exists, the File send handler reports an error and then follows common adapter retry logic for send ports.</span></span> <span data-ttu-id="2bb53-118">此為 FILE 傳送處理常式的預設複製模式。</span><span class="sxs-lookup"><span data-stu-id="2bb53-118">This is a default copy mode for the File send handler.</span></span><br /><br /> <span data-ttu-id="2bb53-119">**覆寫 (2)。**</span><span class="sxs-lookup"><span data-stu-id="2bb53-119">**Overwrite (2).**</span></span> <span data-ttu-id="2bb53-120">若檔案存在，FILE 傳送處理常式會開啟檔案，並覆寫其內容。</span><span class="sxs-lookup"><span data-stu-id="2bb53-120">The File send handler opens a file if it exists and overwrites its content.</span></span> <span data-ttu-id="2bb53-121">若檔案不存在，FILE 傳送處理常式會建立新檔案。</span><span class="sxs-lookup"><span data-stu-id="2bb53-121">If the file does not exist, the File send handler creates a new file.</span></span>|  
|<span data-ttu-id="2bb53-122">**AllowCacheOnWrite**</span><span class="sxs-lookup"><span data-stu-id="2bb53-122">**AllowCacheOnWrite**</span></span>|<span data-ttu-id="2bb53-123">xs:Boolean</span><span class="sxs-lookup"><span data-stu-id="2bb53-123">xs:Boolean</span></span>|<span data-ttu-id="2bb53-124">定義將訊息寫入檔案時，FILE 配接器是否使用檔案系統快取。</span><span class="sxs-lookup"><span data-stu-id="2bb53-124">Defines whether the File adapter uses file system caching when writing messages to a file.</span></span>|  
|<span data-ttu-id="2bb53-125">**ReceivedFileName**</span><span class="sxs-lookup"><span data-stu-id="2bb53-125">**ReceivedFileName**</span></span>|<span data-ttu-id="2bb53-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="2bb53-126">xs:string</span></span>|<span data-ttu-id="2bb53-127">定義 FILE 配接器從中讀取訊息之檔案的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="2bb53-127">Defines the full name of the file from which the File adapter reads the message.</span></span>|  
|<span data-ttu-id="2bb53-128">**FileCreationTime**</span><span class="sxs-lookup"><span data-stu-id="2bb53-128">**FileCreationTime**</span></span>|<span data-ttu-id="2bb53-129">xs:datetime</span><span class="sxs-lookup"><span data-stu-id="2bb53-129">xs:datetime</span></span>|<span data-ttu-id="2bb53-130">定義檔案寫入由 FILE 接收配接器監控之資料夾的時間。</span><span class="sxs-lookup"><span data-stu-id="2bb53-130">Defines the time that the file was written to the folder that is monitored by the File receive adapter.</span></span>|  
|<span data-ttu-id="2bb53-131">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="2bb53-131">**Username**</span></span>|<span data-ttu-id="2bb53-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="2bb53-132">xs:string</span></span>|<span data-ttu-id="2bb53-133">定義當指定替代認證來存取網路共用時所使用的帳戶使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="2bb53-133">Defines the user name for the account used when specifying alternative credentials to access a network share.</span></span>|  
|<span data-ttu-id="2bb53-134">**密碼**</span><span class="sxs-lookup"><span data-stu-id="2bb53-134">**Password**</span></span>|<span data-ttu-id="2bb53-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="2bb53-135">xs:string</span></span>|<span data-ttu-id="2bb53-136">定義當指定替代認證來存取網路共用時所使用的帳戶密碼。</span><span class="sxs-lookup"><span data-stu-id="2bb53-136">Defines the password for the account used when specifying alternative credentials to access a network share.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bb53-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bb53-137">See Also</span></span>  
 [<span data-ttu-id="2bb53-138">設定 File 配接器</span><span class="sxs-lookup"><span data-stu-id="2bb53-138">Configuring the File Adapter</span></span>](../core/configure-the-file-adapter.md)