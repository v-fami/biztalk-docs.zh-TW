---
title: "SchemaValidator |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, SchemaValidator utility
- validating, SchemaValidator utility
- SchemaValidator utility
- schemas, SchemaValidator utility
ms.assetid: 3bd61a03-d81e-4fd1-802c-f801000002d7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c25615c2efcb37ebfc6083bc09d48c7fc1506217
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schemavalidator"></a><span data-ttu-id="2dd01-102">SchemaValidator</span><span class="sxs-lookup"><span data-stu-id="2dd01-102">SchemaValidator</span></span>
<span data-ttu-id="2dd01-103">您可以使用 SchemaValidator 公用程式，疑難排解訊息執行個體的問題。</span><span class="sxs-lookup"><span data-stu-id="2dd01-103">You use the SchemaValidator utility to troubleshoot problems with a message instance.</span></span> <span data-ttu-id="2dd01-104">如果您收到驗證失敗的訊息，可以執行 SchemaValidator 公用程式找出失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="2dd01-104">If you receive a message that fails validation, you can run the SchemaValidator utility to determine the source of the failure.</span></span>  
  
 <span data-ttu-id="2dd01-105">如果要使用含有結構描述 .dll 檔的組件，並且您沒有結構描述 .xsd 檔，請使用這個公用程式。</span><span class="sxs-lookup"><span data-stu-id="2dd01-105">You use this utility if you are using an assembly that includes a schema .dll file, and you do not have a schema .xsd file.</span></span> <span data-ttu-id="2dd01-106">SchemaValidator 公用程式讓您可以使用結構描述 .dll 檔進行驗證。</span><span class="sxs-lookup"><span data-stu-id="2dd01-106">The SchemaValidator utility lets you validate using the schema .dll file.</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="2dd01-107">SDK 中的位置</span><span class="sxs-lookup"><span data-stu-id="2dd01-107">Location in SDK</span></span>  
 <span data-ttu-id="2dd01-108">\<*磁碟機*> \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\SchemaValidator</span><span class="sxs-lookup"><span data-stu-id="2dd01-108">\<*drive*>\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\SchemaValidator</span></span>  
  
## <a name="building-and-running-schemavalidator"></a><span data-ttu-id="2dd01-109">建置和執行 SchemaValidator</span><span class="sxs-lookup"><span data-stu-id="2dd01-109">Building and Running SchemaValidator</span></span>  
  
#### <a name="to-build-the-schemavalidator-utility"></a><span data-ttu-id="2dd01-110">建置 SchemaValidator 公用程式</span><span class="sxs-lookup"><span data-stu-id="2dd01-110">To build the SchemaValidator utility</span></span>  
  
1.  <span data-ttu-id="2dd01-111">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="2dd01-111">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="2dd01-112">移至\<*磁碟機*> \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\SchemaValidator。</span><span class="sxs-lookup"><span data-stu-id="2dd01-112">Move to \<*drive*>\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\SchemaValidator.</span></span>  
  
3.  <span data-ttu-id="2dd01-113">在命令提示字元中，輸入**sn-k SchemaValidator.snk**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="2dd01-113">At the command prompt, type **sn -k SchemaValidator.snk**, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="2dd01-114">啟動**Microsoft Visual Studio 2012**。</span><span class="sxs-lookup"><span data-stu-id="2dd01-114">Start **Microsoft Visual Studio 2012**.</span></span>  
  
5.  <span data-ttu-id="2dd01-115">在**檔案**功能表上，指向**開啟**，然後按一下 **開啟的方案**。</span><span class="sxs-lookup"><span data-stu-id="2dd01-115">On the **File** menu, point to **Open**, and then click **Open Solution**.</span></span>  
  
6.  <span data-ttu-id="2dd01-116">移至\<*磁碟機*> \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\SchemaValidator，選取**SchemaValidator.sln**，然後按一下按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="2dd01-116">Move to \<*drive*>\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\SchemaValidator, select **SchemaValidator.sln**, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="2dd01-117">在 方案總管 中，以滑鼠右鍵按一下**SchemaValidator**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="2dd01-117">In Solution Explorer, right-click **SchemaValidator**, and then click **Properties**.</span></span>  
  
8.  <span data-ttu-id="2dd01-118">在**MessageInspector 屬性**頁面上，按一下**簽署**索引標籤，然後再按一下**簽署組件**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2dd01-118">In the **MessageInspector Property**  page, click **Signing** tab, and then click **Sign the assembly** checkbox.</span></span> <span data-ttu-id="2dd01-119">選取**SchemaValidator.snk**中**選擇強式名稱金鑰檔**。</span><span class="sxs-lookup"><span data-stu-id="2dd01-119">Select **SchemaValidator.snk** in **Choose a strong name key file**.</span></span>  
  
9. <span data-ttu-id="2dd01-120">按一下**SchemaValidator.cs**。</span><span class="sxs-lookup"><span data-stu-id="2dd01-120">Click **SchemaValidator.cs**.</span></span>  
  
10. <span data-ttu-id="2dd01-121">在下列 `Main` 的現有程式碼行中，輸入適當的訊息執行個體路徑：</span><span class="sxs-lookup"><span data-stu-id="2dd01-121">Type the appropriate message instance path in the following existing line of code in `Main`:</span></span>  
  
    ```  
    const string xmlInstancePath = @"..\..\Sample3A4.xml";  
    ```  
  
11. <span data-ttu-id="2dd01-122">使用 RNPIP 組件的參考取代下列 `Main` 中的現有程式碼行，然後選取適當的結構描述：</span><span class="sxs-lookup"><span data-stu-id="2dd01-122">Replace the following existing line of code in `Main` with a reference to the RNPIPs assembly, and then select the appropriate schema:</span></span>  
  
    ```  
    _3A4_MS_V02_02_PurchaseOrderRequest BTSSchema = new _3A4_MS_V02_02_PurchaseOrderRequest();  
    ```  
  
12. <span data-ttu-id="2dd01-123">以滑鼠右鍵按一下**SchemaValidator**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="2dd01-123">Right-click **SchemaValidator**, and then click **Build**.</span></span>  
  
13. <span data-ttu-id="2dd01-124">修改訊息執行個體至您想要藉由移除測試\< \!DOCTYPE … > 標記指定 DTD 檔案，從 XML 執行個體的標頭。</span><span class="sxs-lookup"><span data-stu-id="2dd01-124">Modify the message instance to you want to test by removing the \<\!DOCTYPE …> tag specifying the DTD file from the header of the XML instance.</span></span>  
  
14. <span data-ttu-id="2dd01-125">在訊息執行個體的根節點中，加入將要進行驗證之結構描述的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="2dd01-125">In the root node of the message instance, add an XML namespace of the schema that you will validate against.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2dd01-126">如需可以由 SchemaValidator 公用程式進行驗證的結構描述的範例，請參閱中的 Sample3A4.xml \<*磁碟機*> \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\SchemaValidator。</span><span class="sxs-lookup"><span data-stu-id="2dd01-126">For an example of a schema ready to be validated by the SchemaValidator utility, see Sample3A4.xml in \<*drive*>\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\SchemaValidator.</span></span>  
  
15. <span data-ttu-id="2dd01-127">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下  **SchemaValidator.cs**，然後按下 CTRL 和 F5 執行公用程式。</span><span class="sxs-lookup"><span data-stu-id="2dd01-127">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **SchemaValidator.cs**, and then press CTRL and F5 to run the utility.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2dd01-128">備註</span><span class="sxs-lookup"><span data-stu-id="2dd01-128">Remarks</span></span>  
 <span data-ttu-id="2dd01-129">由於 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含 SchemaValidator 程式碼，因此您可以在公用程式中加入邏輯。</span><span class="sxs-lookup"><span data-stu-id="2dd01-129">Because the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes the SchemaValidator code, you can add logic to the utility.</span></span> <span data-ttu-id="2dd01-130">例如，您可以讓公用程式成為命令列公用程式。</span><span class="sxs-lookup"><span data-stu-id="2dd01-130">For example, you can make it a command-line utility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd01-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dd01-131">See Also</span></span>  
 [<span data-ttu-id="2dd01-132">公用程式</span><span class="sxs-lookup"><span data-stu-id="2dd01-132">Utilities</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)