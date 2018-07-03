---
title: 一般疑難排解問答集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2f89d92-0a97-4017-8b8e-6afd8b20eaf4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a47cfd0bc1d2de1ad044712c12b97260981e610
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010647"
---
# <a name="general-troubleshooting-questions-and-answers"></a><span data-ttu-id="6dcf3-102">一般疑難排解問答集</span><span class="sxs-lookup"><span data-stu-id="6dcf3-102">General Troubleshooting Questions and Answers</span></span>
<span data-ttu-id="6dcf3-103">本主題有問題和解答，以便協助您解決問題的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-103">This topic has questions and answers to help you resolve issues with the BizTalk Mapper.</span></span>  
  
## <a name="how-do-i-specify-xslt-output-settings"></a><span data-ttu-id="6dcf3-104">我該如何指定 XSLT 輸出設定？</span><span class="sxs-lookup"><span data-stu-id="6dcf3-104">How do I specify XSLT output settings?</span></span>  
 <span data-ttu-id="6dcf3-105">您可以使用 BizTalk 對應工具加入或省略 XML 宣告，並控制輸出執行個體資料所使用的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-105">You can use the BizTalk Mapper to include or omit XML declarations, and control the encoding used for output instance data.</span></span>  
  
#### <a name="include-or-exclude-an-xml-declaration"></a><span data-ttu-id="6dcf3-106">包含或排除 XML 宣告</span><span class="sxs-lookup"><span data-stu-id="6dcf3-106">Include or exclude an XML declaration</span></span>  
  
1.  <span data-ttu-id="6dcf3-107">在 [格線] 檢視中，按一下對應工具格線。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-107">In the Grid view, click the mapper grid.</span></span> <span data-ttu-id="6dcf3-108">**屬性**視窗會顯示格線屬性。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-108">The **Properties** window displays the grid properties.</span></span>  
  
2.  <span data-ttu-id="6dcf3-109">中的下拉式清單**省略 XML 宣告**屬性中，選取**是**省略 XML 宣告，或選取**No**不表示省略 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-109">In the drop-down list for the **Omit XML Declaration** property, select **Yes** to omit an XML declaration, or select **No** not to omit an XML declaration.</span></span>  
  
#### <a name="set-encoding-for-output-instance-data"></a><span data-ttu-id="6dcf3-110">設定編碼方式輸出執行個體資料</span><span class="sxs-lookup"><span data-stu-id="6dcf3-110">Set encoding for output instance data</span></span>  
  
1.  <span data-ttu-id="6dcf3-111">在 [格線] 檢視中，按一下對應工具格線。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-111">In the Grid view, click the mapper grid.</span></span> <span data-ttu-id="6dcf3-112">**屬性**視窗會顯示格線屬性。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-112">The **Properties** window displays the grid properties.</span></span>  
  
2.  <span data-ttu-id="6dcf3-113">中的下拉式清單**XSLT 編碼**屬性中，選取您要字元集要用於輸出執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-113">In the drop-down list for the **XSLT Encoding** property, select the character set you want to use for the output instance data.</span></span>  
  
## <a name="how-do-i-create-multipart-mappings"></a><span data-ttu-id="6dcf3-114">我該如何建立多部分對應？</span><span class="sxs-lookup"><span data-stu-id="6dcf3-114">How do I create multipart mappings?</span></span>  
 <span data-ttu-id="6dcf3-115">如果您有多個對應搭配使用時，您必須將它們結合在協調流程中，使用**轉換**圖形一起測試。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-115">If you have multiple maps that are used together, you will need to combine them in an orchestration by using the **Transform** shape to test them together.</span></span> <span data-ttu-id="6dcf3-116">BizTalk 對應工具一次只能測試一個對應。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-116">The BizTalk Mapper can test only one map at a time.</span></span>  
  
## <a name="why-isnt-my-database-functoid-working"></a><span data-ttu-id="6dcf3-117">為何我的資料庫運算質沒有作用？</span><span class="sxs-lookup"><span data-stu-id="6dcf3-117">Why isn't my database functoid working?</span></span>  
 <span data-ttu-id="6dcf3-118">資料庫運算質**資料庫尋查**並**值擷取程式 」** 不會直接傳回錯誤資訊; 相反地，它們擷取資訊並將其提供給**錯誤傳回**運算質，以供您的對應。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-118">The database functoids **Database Lookup** and **Value Extractor** do not directly return error information; rather, they capture the information and supply it to the **Error Return** functoid for use by your map.</span></span> <span data-ttu-id="6dcf3-119">您可以使用**錯誤傳回**」 運算質進行錯誤偵測，在下列案例：</span><span class="sxs-lookup"><span data-stu-id="6dcf3-119">You can use the **Error Return** functoid for error detection as in the following scenarios:</span></span>  
  
- <span data-ttu-id="6dcf3-120">當您的對應具有**資料庫尋查**或是**值擷取程式 」** 表現不如預期的運算質。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-120">When your map has a **Database Lookup** or **Value Extractor** functoid that is not behaving as expected.</span></span> <span data-ttu-id="6dcf3-121">若要查看錯誤訊息，請暫時將運算質對應至輸出結構描述中的欄位。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-121">To see the error message, temporarily map the functoid to a field in the output schema.</span></span>  
  
- <span data-ttu-id="6dcf3-122">如果在資料庫作業失敗時，您的應用程式預期不同的訊息內容。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-122">If your application expects different message content when database operations fail.</span></span> <span data-ttu-id="6dcf3-123">您可以使用**錯誤傳回**」 運算質偵測錯誤，並將錯誤訊息對應到替代的結構，如此下游應用程式可以反應以節制的方式。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-123">You can use the **Error Return** functoid to detect an error and map the error message to an alternate structure so that downstream applications can react in a controlled manner.</span></span>  
  
  <span data-ttu-id="6dcf3-124">若要避免只在執行階段偵測到的錯誤，請確定的第一個參數**錯誤傳回**運算質會輸出**資料庫尋查**運算質和不在任何其他運算質的輸出Database 類別目錄。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-124">To avoid errors that are detected only at run time, make sure that the first parameter to the **Error Return** functoid is the output of a **Database Lookup** functoid and not the output of any other functoid in the Database category.</span></span>  
  
  <span data-ttu-id="6dcf3-125">如需使用詳細資訊**錯誤傳回**運算質 （包括範例），請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-125">For more information about using the **Error Return** functoid (including a sample), see the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="why-is-my-map-failing-when-calling-my-custom-functoid"></a><span data-ttu-id="6dcf3-126">為何我的對應會在呼叫自訂運算質時失敗？</span><span class="sxs-lookup"><span data-stu-id="6dcf3-126">Why is my map failing when calling my custom functoid?</span></span>  
 <span data-ttu-id="6dcf3-127">自訂運算質必須先安裝到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上的全域組件快取 (GAC)，才能夠由對應叫用。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-127">Custom functoids must be installed into the global assembly cache (GAC) on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer before they can be invoked by a map.</span></span> <span data-ttu-id="6dcf3-128">請確認包含自訂運算質的組件，已經獲得簽署並放置到 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-128">Verify that the assembly containing your custom functoid has been signed and placed into the GAC.</span></span> <span data-ttu-id="6dcf3-129">另外，將組件複製到資料夾 “%BTSINSTALLPATH%\Developer Tools\Mapper Extensions” 中。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-129">Also, copy the assembly into the folder “%BTSINSTALLPATH%\Developer Tools\Mapper Extensions”.</span></span>  
  
 <span data-ttu-id="6dcf3-130">如需有關如何安裝至 GAC 的組件的詳細資訊，請參閱[組件安裝在 GAC 中](../core/assembly-installation-in-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-130">For more information about installing assemblies to the GAC, see [Assembly Installation in the GAC](../core/assembly-installation-in-the-gac.md).</span></span> <span data-ttu-id="6dcf3-131">若要檢視安裝在 GAC 中的組件，請瀏覽至您 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 安裝目錄的 Assembly 目錄。</span><span class="sxs-lookup"><span data-stu-id="6dcf3-131">To view assemblies installed in the GAC, navigate to the Assembly directory of your [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] installation directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dcf3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dcf3-132">See Also</span></span>  
 [<span data-ttu-id="6dcf3-133">地圖疑難排解</span><span class="sxs-lookup"><span data-stu-id="6dcf3-133">Troubleshooting Maps</span></span>](../core/troubleshooting-maps.md)