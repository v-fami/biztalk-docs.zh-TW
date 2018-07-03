---
title: 設定 File 配接器的限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [File adapters], restrictions
- File adapters, restrictions
ms.assetid: 8d8137a7-5b16-4ae3-a0a7-6d114324bdf3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04b5f5e025b1e6b399834c1b327900b1fbe62cf4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000335"
---
# <a name="restrictions-when-configuring-the-file-adapter"></a><span data-ttu-id="0c89b-102">設定 File 配接器的限制</span><span class="sxs-lookup"><span data-stu-id="0c89b-102">Restrictions when configuring the File adapter</span></span>
<span data-ttu-id="0c89b-103">限制和規則使用 file 配接器時。</span><span class="sxs-lookup"><span data-stu-id="0c89b-103">Restrictions and rules when using the file adapter.</span></span>

## <a name="file-mask-and-file-name-gotchas"></a><span data-ttu-id="0c89b-104">檔案遮罩和檔案名稱錯誤</span><span class="sxs-lookup"><span data-stu-id="0c89b-104">File mask and file name gotchas</span></span>

<span data-ttu-id="0c89b-105">檔案遮罩是一個字串，指定 FILE 接收處理常式從接收位置拾取的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="0c89b-105">The file mask is a string that specifies the type of file that the File receive handler will pick up from the receive location.</span></span> <span data-ttu-id="0c89b-106">檔案名稱是一個字串，指定 FILE 傳送處理常式寫入訊息的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0c89b-106">The file name is a string that specifies the name of the file where the File send handler will write the message.</span></span>  
  
 <span data-ttu-id="0c89b-107">下列限制適用於檔案名稱和檔案遮罩屬性：</span><span class="sxs-lookup"><span data-stu-id="0c89b-107">The following restrictions apply to the file name and file mask properties:</span></span>  
  
- <span data-ttu-id="0c89b-108">每個接收位置或傳送埠只能指定一個檔案遮罩或一個檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0c89b-108">Only one file mask or file name can be specified per receive location or send port.</span></span>  
  
- <span data-ttu-id="0c89b-109">不允許完整路徑或部分路徑加上檔案遮罩或檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0c89b-109">The full path or part of the path along with the file mask or file name is not allowed.</span></span> <span data-ttu-id="0c89b-110">檔案遮罩和檔案名稱永遠代表不含路徑的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c89b-110">The file mask and file name always represent a name without the path.</span></span>  
  
- <span data-ttu-id="0c89b-111">檔案遮罩和檔案名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0c89b-111">The file mask and file name are not case-sensitive.</span></span>  
  
- <span data-ttu-id="0c89b-112">檔案名稱不能包含任何下列字元： \< \> : / &#124; 」？</span><span class="sxs-lookup"><span data-stu-id="0c89b-112">The file name cannot contain any of the following characters: \< \> : / &#124; " ?</span></span> <span data-ttu-id="0c89b-113">\* ;</span><span class="sxs-lookup"><span data-stu-id="0c89b-113">\* ;</span></span>  
  
- <span data-ttu-id="0c89b-114">檔案遮罩不能包含任何下列字元： \< \> : / &#124; ";</span><span class="sxs-lookup"><span data-stu-id="0c89b-114">The file mask cannot contain any of the following characters: \< \> : / &#124; " ;</span></span> 
  
- <span data-ttu-id="0c89b-115">下列保留的裝置名稱不能做為檔案名稱： CON、 PRN、 AUX、 時鐘 $、 NUL、 COM1、 COM2、 COM3、 COM4、 COM5、 COM6、 COM7、 COM8、 COM9、 LPT1、 LPT2、 LPT3、 LPT4、 LPT5、 LPT6、 LPT7、 LPT8 和 LPT9。</span><span class="sxs-lookup"><span data-stu-id="0c89b-115">The following reserved device names cannot be used as the name of a file: CON, PRN, AUX, CLOCK$, NUL, COM1, COM2, COM3, COM4, COM5, COM6, COM7, COM8, COM9, LPT1, LPT2, LPT3, LPT4, LPT5, LPT6, LPT7, LPT8, and LPT9.</span></span> <span data-ttu-id="0c89b-116">此外，也不允許這些名稱與副檔名的任何組合。</span><span class="sxs-lookup"><span data-stu-id="0c89b-116">In addition, any combinations of these with extensions are not allowed.</span></span>  
  
- <span data-ttu-id="0c89b-117">Windows 磁碟區使用 8.3 (8.3) 命名慣例，根據預設，會使用簡短和長檔名。</span><span class="sxs-lookup"><span data-stu-id="0c89b-117">Windows disk volumes use the 8.3 (8dot3) naming convention by default, which uses short and long file names.</span></span> <span data-ttu-id="0c89b-118">非系統磁碟區停用 8.3 命名慣例，並因此只能使用長檔名。</span><span class="sxs-lookup"><span data-stu-id="0c89b-118">Non-system disk volumes disable the 8dot3 naming convention, and therefore only use long file names.</span></span> 

  <span data-ttu-id="0c89b-119">啟用 8.3 時，檔案和其副檔名取得轉換為簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="0c89b-119">When 8dot3 is enabled, files and their file extensions get converted to a short name.</span></span> <span data-ttu-id="0c89b-120">例如，`testabcdefgh.docx`取得轉換成`testab~1.doc`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-120">For example, `testabcdefgh.docx` gets converted to `testab~1.doc`.</span></span> <span data-ttu-id="0c89b-121">請注意，已縮短檔案名稱，並已從縮短檔案延伸模組`.docx`至`doc`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-121">Notice that file name is shortened, and the file extension is shortened from `.docx` to `doc`.</span></span>

  <span data-ttu-id="0c89b-122">此行為會影響 File 配接器接收檔案的方式。</span><span class="sxs-lookup"><span data-stu-id="0c89b-122">This behavior impacts how the File adapter receives file.</span></span> <span data-ttu-id="0c89b-123">如果檔案遮罩之所以設為`*.xml`，然後檔案 比對兩者`*.xml`和`*.xmln`延伸模組會挑選。</span><span class="sxs-lookup"><span data-stu-id="0c89b-123">If a file mask is set to `*.xml`, then files matching both `*.xml` and `*.xmln` extensions are picked up.</span></span> 

  <span data-ttu-id="0c89b-124">若要查看您的磁碟上是否已啟用 8.3 命名慣例，開啟命令提示字元做為系統管理員，然後輸入`fsutil 8dot3name query c:`，或`fsutil 8dot3name query d:`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="0c89b-124">To see if the 8dot3 naming convention is enabled on your disks, open a command prompt as Administrator, and type `fsutil 8dot3name query c:`, or `fsutil 8dot3name query d:`, and so on.</span></span> <span data-ttu-id="0c89b-125">範例輸出看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="0c89b-125">Sample output looks like the following:</span></span>

  ```
  C:\WINDOWS\system32>fsutil 8dot3name query c:
  The volume state is: 0 (8dot3 name creation is enabled).
  The registry state is: 2 (Per volume setting - the default).
    
  Based on the above two settings, 8dot3 name creation is enabled on c:
  ```
    
  <span data-ttu-id="0c89b-126">File 配接器會使用[FindFirstFile 函式](https://msdn.microsoft.com/library/windows/desktop/aa364418(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="0c89b-126">The File adapter uses the [FindFirstFile function](https://msdn.microsoft.com/library/windows/desktop/aa364418(v=vs.85).aspx).</span></span> <span data-ttu-id="0c89b-127">此函式會包含具有短期和長期的檔案名稱的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="0c89b-127">This function includes search results that have the short and long file names.</span></span> <span data-ttu-id="0c89b-128">若要查看資料夾中的短期和長期的檔案名稱，開啟命令提示字元，移至您的資料夾，並輸入`dir /x`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-128">To see the short and long file names in a folder, open a command prompt, go to your folder, and type `dir /x`.</span></span> <span data-ttu-id="0c89b-129">在命令提示字元中，您也可以輸入`dir c:\foldername /x`。</span><span class="sxs-lookup"><span data-stu-id="0c89b-129">In a command prompt, you can also type `dir c:\foldername /x`.</span></span>
    
  <span data-ttu-id="0c89b-130">如果您變更 8dot3name （英文） 上的設定磁碟區時，新的檔案就會使用新的設定。</span><span class="sxs-lookup"><span data-stu-id="0c89b-130">If you change the 8dot3name setting on a volume, then new files use the new setting.</span></span> <span data-ttu-id="0c89b-131">任何現有的檔案會保留其名稱，直到會跟著移動。</span><span class="sxs-lookup"><span data-stu-id="0c89b-131">Any existing files keep their names until they are moved.</span></span> 
    
  <span data-ttu-id="0c89b-132">若要只挑選您預期的檔案，並在高負載期間取得較佳的效能 （較少額外負荷），則可能最好設定 File 配接器使用的磁碟區會在停用 8dot3name （英文）。</span><span class="sxs-lookup"><span data-stu-id="0c89b-132">To only pick up your intended files, and to get better performance (less overhead) during higher load, then it may be best to configure the File adapter to use a volume where 8dot3name is disabled.</span></span> 
  
- <span data-ttu-id="0c89b-133">檔案路徑、檔案遮罩和檔案名稱 (不含巨集替代) 的總長度不可超過 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="0c89b-133">The total length of the file path, file mask, and file name (without macro substitution) must not exceed 256 characters.</span></span> <span data-ttu-id="0c89b-134">(這是 MessageBox 資料庫的限制。)</span><span class="sxs-lookup"><span data-stu-id="0c89b-134">(This is a restriction of the MessageBox database.)</span></span>  
  
- <span data-ttu-id="0c89b-135">檔案路徑不能以 "`\\`?" 開頭。</span><span class="sxs-lookup"><span data-stu-id="0c89b-135">The file path cannot begin with "`\\`?".</span></span>  
  
- <span data-ttu-id="0c89b-136">對應的網路磁碟機代號不能用於檔案路徑，因為他們是以使用者工作階段為基礎。</span><span class="sxs-lookup"><span data-stu-id="0c89b-136">Mapped network drive letters cannot be used in the file path, because they are user session based.</span></span>  
  
  <span data-ttu-id="0c89b-137">「BizTalk 傳訊引擎」永遠會使用先前列示的項目，在設計階段驗證檔案名稱和檔案遮罩屬性。</span><span class="sxs-lookup"><span data-stu-id="0c89b-137">The BizTalk Messaging Engine always validates the file name and file mask properties at design time by using the items previously listed.</span></span> <span data-ttu-id="0c89b-138">此外，若配接器在動態連接埠上傳送訊息，FILE 配接器會在執行階段驗證檔案名稱和檔案遮罩屬性。</span><span class="sxs-lookup"><span data-stu-id="0c89b-138">In addition, the File adapter validates the file name and file mask properties at run time if the adapter sends the message on a dynamic port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c89b-139">FILE 配接器不會拾取系統檔案或唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="0c89b-139">The File adapter does not pick up system files or read-only files.</span></span> <span data-ttu-id="0c89b-140">只會拾取硬碟的檔案，不會拾取裝置檔案。</span><span class="sxs-lookup"><span data-stu-id="0c89b-140">Only disk-based files are picked up, and not device files.</span></span>  

## <a name="using-macros-in-file-names"></a><span data-ttu-id="0c89b-141">在 檔案名稱使用巨集</span><span class="sxs-lookup"><span data-stu-id="0c89b-141">Using macros in file names</span></span>

<span data-ttu-id="0c89b-142">您可以使用一組預先定義的巨集，以動態建立 FILE 傳送處理常式在其中寫入訊息的檔案。</span><span class="sxs-lookup"><span data-stu-id="0c89b-142">You can use a predefined set of macros to dynamically create the files in which the File send handler writes messages.</span></span> <span data-ttu-id="0c89b-143">在檔案系統上建立檔案之前，FILE 傳送處理常式會以其個別的值取代檔案名稱中的所有巨集。</span><span class="sxs-lookup"><span data-stu-id="0c89b-143">Before creating a file on the file system, the File send handler replaces all the macros in the file name with their individual values.</span></span> <span data-ttu-id="0c89b-144">您可以在一個檔案名稱中使用數個不同的巨集。</span><span class="sxs-lookup"><span data-stu-id="0c89b-144">You can use several different macros in one file name.</span></span>  
  
 <span data-ttu-id="0c89b-145">在使用 BizTalk 總管物件模型設定 FILE 傳送處理常式時，可以使用檔案名稱巨集。</span><span class="sxs-lookup"><span data-stu-id="0c89b-145">You can use the file name macros while configuring the File send handler using the BizTalk Explorer object model.</span></span>  
  
 <span data-ttu-id="0c89b-146">若發生下列任何一種情況，FILE 傳送處理常式就不會以值取代巨集：</span><span class="sxs-lookup"><span data-stu-id="0c89b-146">The File send handler does not replace the macros with a value if any of the following are true:</span></span>  
  
- <span data-ttu-id="0c89b-147">未設定對應的系統屬性。</span><span class="sxs-lookup"><span data-stu-id="0c89b-147">The corresponding system property is not set.</span></span>  
  
- <span data-ttu-id="0c89b-148">巨集拼錯。</span><span class="sxs-lookup"><span data-stu-id="0c89b-148">The macro is misspelled.</span></span>  
  
- <span data-ttu-id="0c89b-149">巨集的值包含檔案名稱中無效的符號。</span><span class="sxs-lookup"><span data-stu-id="0c89b-149">The value for the macro contains symbols that are not valid in the file name.</span></span>  
  
  <span data-ttu-id="0c89b-150">若發生這些情況中的任何一項，FILE 傳送處理常式就會將檔案名稱中的巨集保留原狀，例如 Myfile_%MessageID%.xml。</span><span class="sxs-lookup"><span data-stu-id="0c89b-150">If any of these conditions occur, the File send handler leaves the macros in the file name untouched, for example Myfile_%MessageID%.xml.</span></span>  
  
  <span data-ttu-id="0c89b-151">下表列出支援的巨集，並描述 FILE 傳送處理常式如何取代它們。</span><span class="sxs-lookup"><span data-stu-id="0c89b-151">The following table lists the supported macros and describes how the File send handler replaces them.</span></span>  
  
|<span data-ttu-id="0c89b-152">巨集名稱</span><span class="sxs-lookup"><span data-stu-id="0c89b-152">Macro name</span></span>|<span data-ttu-id="0c89b-153">取代值</span><span class="sxs-lookup"><span data-stu-id="0c89b-153">Substitute value</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="0c89b-154">%datetime%</span><span class="sxs-lookup"><span data-stu-id="0c89b-154">%datetime%</span></span>|<span data-ttu-id="0c89b-155">Coordinated Universal Time (UTC) 日期時間格式為 YYYY-MM-DDThhmmss (例如，1997-07-12T103508)。</span><span class="sxs-lookup"><span data-stu-id="0c89b-155">Coordinated Universal Time (UTC) date time in the format YYYY-MM-DDThhmmss (for example, 1997-07-12T103508).</span></span>|  
|<span data-ttu-id="0c89b-156">%datetime_bts2000%</span><span class="sxs-lookup"><span data-stu-id="0c89b-156">%datetime_bts2000%</span></span>|<span data-ttu-id="0c89b-157">UTC 日期時間的格式為 YYYYMMDDhhmmsss，其中 sss 表示秒與毫秒 (例如，199707121035234 表示 1997/07/12，10:35:23 與 400 毫秒)。</span><span class="sxs-lookup"><span data-stu-id="0c89b-157">UTC date time in the format YYYYMMDDhhmmsss, where sss means seconds and milliseconds (for example, 199707121035234 means 1997/07/12, 10:35:23 and 400 milliseconds).</span></span>|  
|<span data-ttu-id="0c89b-158">%datetime.tz%</span><span class="sxs-lookup"><span data-stu-id="0c89b-158">%datetime.tz%</span></span>|<span data-ttu-id="0c89b-159">本地日期時間加上 GMT 的時區，格式為 YYYY-MM-DDThhmmssTZD (例如，1997-07-12T103508+800)。</span><span class="sxs-lookup"><span data-stu-id="0c89b-159">Local date time plus time zone from GMT in the format YYYY-MM-DDThhmmssTZD, (for example, 1997-07-12T103508+800).</span></span>|  
|<span data-ttu-id="0c89b-160">%DestinationParty%</span><span class="sxs-lookup"><span data-stu-id="0c89b-160">%DestinationParty%</span></span>|<span data-ttu-id="0c89b-161">目的地合作對象的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c89b-161">Name of the destination party.</span></span> <span data-ttu-id="0c89b-162">這個值來自訊息內容屬性 **BTS.DestinationParty**。</span><span class="sxs-lookup"><span data-stu-id="0c89b-162">The value comes from the message context property **BTS.DestinationParty**.</span></span>|  
|<span data-ttu-id="0c89b-163">%DestinationPartyQualifier%</span><span class="sxs-lookup"><span data-stu-id="0c89b-163">%DestinationPartyQualifier%</span></span>|<span data-ttu-id="0c89b-164">目的地合作對象的辨識符號。</span><span class="sxs-lookup"><span data-stu-id="0c89b-164">Qualifier of the destination party.</span></span> <span data-ttu-id="0c89b-165">這個值來自訊息內容屬性 **BTS.DestinationPartyQualifier**。</span><span class="sxs-lookup"><span data-stu-id="0c89b-165">The value comes from the message context property **BTS.DestinationPartyQualifier**.</span></span>|  
|<span data-ttu-id="0c89b-166">%MessageID%</span><span class="sxs-lookup"><span data-stu-id="0c89b-166">%MessageID%</span></span>|<span data-ttu-id="0c89b-167">BizTalk Server 中訊息的全域唯一識別碼 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="0c89b-167">Globally unique identifier (GUID) of the message in BizTalk Server.</span></span> <span data-ttu-id="0c89b-168">值是直接來自訊息內容屬性**BTS。MessageID**。</span><span class="sxs-lookup"><span data-stu-id="0c89b-168">The value comes directly from the message context property **BTS.MessageID**.</span></span>|  
|<span data-ttu-id="0c89b-169">%SourceFileName%</span><span class="sxs-lookup"><span data-stu-id="0c89b-169">%SourceFileName%</span></span>|<span data-ttu-id="0c89b-170">FILE 配接器從中讀取訊息的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0c89b-170">Name of the file from which the File adapter read the message.</span></span> <span data-ttu-id="0c89b-171">檔案名稱包含副檔名但排除檔案路徑，例如 Sample.xml。</span><span class="sxs-lookup"><span data-stu-id="0c89b-171">The file name includes the extension and excludes the file path, for example, Sample.xml.</span></span> <span data-ttu-id="0c89b-172">File 配接器時取代這個屬性，從儲存在的絕對檔案路徑擷取檔案名稱**檔案。ReceivedFileName**內容屬性。</span><span class="sxs-lookup"><span data-stu-id="0c89b-172">When substituting this property, the File adapter extracts the file name from the absolute file path stored in the **FILE.ReceivedFileName** context property.</span></span> <span data-ttu-id="0c89b-173">如果內容屬性沒有值 — 比方說，如果在 File 配接器以外的配接器收到的訊息-巨集不會替換，而將保留在檔案名稱 (例如 C:\Drop\\SourceFileName %)。</span><span class="sxs-lookup"><span data-stu-id="0c89b-173">If the context property does not have a value—for example, if a message was received on an adapter other than the File adapter—the macro will not be substituted and will remain in the file name as is (for example, C:\Drop\\%SourceFileName%).</span></span> <span data-ttu-id="0c89b-174">**注意：** 正確實作此巨集需要的輸出訊息和接收的訊息相同的訊息。</span><span class="sxs-lookup"><span data-stu-id="0c89b-174">**Note:**  Correct implementation of this macro requires that the output message is the same message as the received message.</span></span>|  
|<span data-ttu-id="0c89b-175">%SourceParty%</span><span class="sxs-lookup"><span data-stu-id="0c89b-175">%SourceParty%</span></span>|<span data-ttu-id="0c89b-176">FILE 配接器從中接收訊息的來源合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="0c89b-176">Name of the source party from which the File adapter received the message.</span></span> <span data-ttu-id="0c89b-177">**注意：** 正確實作此巨集需要的輸出訊息和接收的訊息相同的訊息。</span><span class="sxs-lookup"><span data-stu-id="0c89b-177">**Note:**  Correct implementation of this macro requires that the output message is the same message as the received message.</span></span>|  
|<span data-ttu-id="0c89b-178">%SourcePartyQualifier%</span><span class="sxs-lookup"><span data-stu-id="0c89b-178">%SourcePartyQualifier%</span></span>|<span data-ttu-id="0c89b-179">FILE 配接器從中接收訊息的來源合作對象辨識符號。</span><span class="sxs-lookup"><span data-stu-id="0c89b-179">Qualifier of the source party from which the File adapter received the message.</span></span> <span data-ttu-id="0c89b-180">**注意：** 正確實作此巨集需要的輸出訊息和接收的訊息相同的訊息。</span><span class="sxs-lookup"><span data-stu-id="0c89b-180">**Note:**  Correct implementation of this macro requires that the output message is the same message as the received message.</span></span>|  
|<span data-ttu-id="0c89b-181">%time%</span><span class="sxs-lookup"><span data-stu-id="0c89b-181">%time%</span></span>|<span data-ttu-id="0c89b-182">UTC 時間的格式為 hhmmss。</span><span class="sxs-lookup"><span data-stu-id="0c89b-182">UTC time in the format hhmmss.</span></span>|  
|<span data-ttu-id="0c89b-183">%time.tz%</span><span class="sxs-lookup"><span data-stu-id="0c89b-183">%time.tz%</span></span>|<span data-ttu-id="0c89b-184">本地時間加上 GMT 的時區，格式為 hhmmssTZD (例如，124525+530)。</span><span class="sxs-lookup"><span data-stu-id="0c89b-184">Local time plus time zone from GMT in the format hhmmssTZD (for example, 124525+530).</span></span>|  
  
 
## <a name="receive-folder-and-destination-location-properties-gotchas"></a><span data-ttu-id="0c89b-185">接收資料夾和目的地位置屬性錯誤</span><span class="sxs-lookup"><span data-stu-id="0c89b-185">Receive folder and destination location properties gotchas</span></span>

<span data-ttu-id="0c89b-186">檔案接收位置是一個包含檔案系統或網路共用上之資料夾路徑的字串，而 FILE 接收處理常式會從此路徑讀取檔案。</span><span class="sxs-lookup"><span data-stu-id="0c89b-186">The file receive location is a string that contains a path to a folder on a file system or network share from which the File receive handler reads files.</span></span> <span data-ttu-id="0c89b-187">檔案目的地位置是一個包含檔案系統或網路共用上之資料夾路徑的字串，而 FILE 傳送處理常式會從此路徑寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="0c89b-187">The file destination location is a string that contains a path to a folder on a file system or network share where the File send handler writes files.</span></span>  
  
 <span data-ttu-id="0c89b-188">下列限制適用於接收資料夾和目的地位置屬性：</span><span class="sxs-lookup"><span data-stu-id="0c89b-188">The following restrictions apply to the receive folder and destination location properties:</span></span>  
  
- <span data-ttu-id="0c89b-189">在您指定使用者中的屬性時，不需要有檔案系統或網路共用上的檔案路徑存在。</span><span class="sxs-lookup"><span data-stu-id="0c89b-189">Existence of the file path on a file system or network share is not required at the time when you specify the property in the user.</span></span>  
  
- <span data-ttu-id="0c89b-190">檔案路徑必須永遠是絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="0c89b-190">The file path must always be absolute.</span></span>  
  
- <span data-ttu-id="0c89b-191">您可以藉由使用通用命名慣例 (UNC) 格式指定的檔案路徑 (例如\\ \\ < *server* \> \\ < *共用*\>)。</span><span class="sxs-lookup"><span data-stu-id="0c89b-191">You can specify the file path by using Universal Naming Convention (UNC) format (for example, \\\\<*server*\>\\<*share*\>).</span></span>  
  
- <span data-ttu-id="0c89b-192">如果檔案路徑為 UNC 格式，伺服器名稱必須包含下列字元: ' ~ ！</span><span class="sxs-lookup"><span data-stu-id="0c89b-192">If the file path is in UNC format, the server name must not contain the following characters: \` ~ !</span></span> <span data-ttu-id="0c89b-193">@ # $ ^ & \* ( ) = + [ ] { } \ &#124; ; : ' " , \< \> / ?</span><span class="sxs-lookup"><span data-stu-id="0c89b-193">@ # $ ^ & \* ( ) = + [ ] { } \ &#124; ; : ' " , \< \> / ?</span></span> <span data-ttu-id="0c89b-194">;</span><span class="sxs-lookup"><span data-stu-id="0c89b-194">;</span></span>  
  
- <span data-ttu-id="0c89b-195">您無法使用父代 (\\...\\) 和目前 (\\。\\) 資料夾符號的檔案路徑的任何部分。</span><span class="sxs-lookup"><span data-stu-id="0c89b-195">You cannot use parent (\\..\\) and current (\\.\\) folder symbols in any part of the file path.</span></span>  
  
- <span data-ttu-id="0c89b-196">檔案路徑是不區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="0c89b-196">The file path is not case-sensitive.</span></span>  
  
- <span data-ttu-id="0c89b-197">檔案路徑不能包含任何下列字元： \< \> : / &#124; 」？</span><span class="sxs-lookup"><span data-stu-id="0c89b-197">The file path cannot contain any of the following characters: \< \> : / &#124; " ?</span></span> <span data-ttu-id="0c89b-198">\* ;</span><span class="sxs-lookup"><span data-stu-id="0c89b-198">\* ;</span></span>  
  
- <span data-ttu-id="0c89b-199">檔案路徑內不能使用下列保留的裝置名稱：CON、PRN、AUX、CLOCK$、NUL、COM1、COM2、COM3、COM4、COM5、COM6、COM7、COM8、COM9、LPT1、LPT2、LPT3、LPT4、LPT5、LPT6、LPT7、LPT8 和 LPT9。</span><span class="sxs-lookup"><span data-stu-id="0c89b-199">You cannot use the following reserved device names in the file path: CON, PRN, AUX, CLOCK$, NUL, COM1, COM2, COM3, COM4, COM5, COM6, COM7, COM8, COM9, LPT1, LPT2, LPT3, LPT4, LPT5, LPT6, LPT7, LPT8, and LPT9.</span></span>  
  
- <span data-ttu-id="0c89b-200">檔案路徑、檔案遮罩或檔案名稱 (沒有巨集替代) 的總長度不得超過 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="0c89b-200">Total length of file path, file mask, or file name (without macro substitution) must not exceed 256 characters.</span></span> <span data-ttu-id="0c89b-201">(MessageBox 資料庫設有此限制。)</span><span class="sxs-lookup"><span data-stu-id="0c89b-201">(The MessageBox database imposes this restriction.)</span></span>  
  
- <span data-ttu-id="0c89b-202">File 配接器不支援 Unicode 規格的檔案路徑 (例如，「\\\\？\\")。</span><span class="sxs-lookup"><span data-stu-id="0c89b-202">The File adapter does not support Unicode specification of the file path (for example, "\\\\?\\").</span></span>  
  
  <span data-ttu-id="0c89b-203">在接收配接器屬性上的限制只有：</span><span class="sxs-lookup"><span data-stu-id="0c89b-203">Restrictions on the receive folder property only:</span></span>  
  
- <span data-ttu-id="0c89b-204">沒有設定為使用含有符號連結的 Microsoft Windows NT 分散式檔案系統資料夾的接收資料夾屬性。</span><span class="sxs-lookup"><span data-stu-id="0c89b-204">Do not set the receive folder property to a folder that uses the Microsoft Windows NT Distributed File System with a symbolic link.</span></span> <span data-ttu-id="0c89b-205">如果您使用的 Windows NT 分散式檔案系統，您可以僅使用資料夾含有直接網路路徑，在 File 配接器接收位置。</span><span class="sxs-lookup"><span data-stu-id="0c89b-205">If you are using Windows NT Distributed File System, you can only use folders with straight network paths in File adapter receive locations.</span></span>  
  
- <span data-ttu-id="0c89b-206">當文件傳送到 UNC 路徑，而且您有一部以上的伺服器在 FILE 配接器的接收位置上接收文件時，則只有一部伺服器會收取和處理傳送至該 UNC 路徑的大部分文件。</span><span class="sxs-lookup"><span data-stu-id="0c89b-206">When documents are sent to a UNC path, and you have more than one server receiving documents at the receive location for the File adapter, only one server will pick up and process most of the documents sent to that UNC path.</span></span> <span data-ttu-id="0c89b-207">如需檔案重新命名的詳細資訊，請參閱 < File 接收配接器區段[File 配接器](../core/file-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0c89b-207">For more information about file renaming, see the File Receive Adapter section of [File Adapter](../core/file-adapter.md).</span></span>  
  
  <span data-ttu-id="0c89b-208">僅針對傳送資料夾屬性的限制：</span><span class="sxs-lookup"><span data-stu-id="0c89b-208">Restrictions on the send folder property only:</span></span>  
  
- <span data-ttu-id="0c89b-209">當 FILE 配接器在非伺服器的作業系統 (例如 Microsoft Windows Vista) 上執行時，可能沒有足夠的作業系統資源能同時處理批次中的全部訊息。</span><span class="sxs-lookup"><span data-stu-id="0c89b-209">The file adapter may not have enough operating system resources to process all of the messages in a batch concurrently when running on a non-server operating system like Microsoft Windows Vista.</span></span>  
  
  <span data-ttu-id="0c89b-210">FILE 配接器會使用先前提及的規則，於設計階段驗證檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="0c89b-210">The File adapter validates the file path at design time by using the previously mentioned rules.</span></span> <span data-ttu-id="0c89b-211">此外，若配接器會以 FILE 配接器透過動態連接埠來傳送訊息，則 FILE 配接器會在執行階段驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="0c89b-211">In addition, the File adapter validates the message at run time if the adapter sends the message through a dynamic port with a File adapter.</span></span>  
  
