---
title: "如何使用 BizTalk 一般檔案結構描述精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7cb8b18-266d-422e-bdb8-1efefb6b4c8e
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff7d87959bd39b9040a495022c2b7bf352954848
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-biztalk-flat-file-schema-wizard"></a><span data-ttu-id="99de5-102">如何使用 BizTalk 一般檔案結構描述精靈</span><span class="sxs-lookup"><span data-stu-id="99de5-102">How to Use BizTalk Flat File Schema Wizard</span></span>
<span data-ttu-id="99de5-103">在舊版 BizTalk Server 中，您必須在 BizTalk 結構描述編輯器中手動將註解新增至 XML 結構描述定義語言 (XSD) 結構描述，讓這些結構描述可被「一般檔案管線」元件所瞭解，例如一般檔案解譯器和一般檔案組合器。</span><span class="sxs-lookup"><span data-stu-id="99de5-103">In previous releases of BizTalk Server, you had to manually add the annotations to XML Schema Definition language (XSD) schemas in the BizTalk Schema Editor to make these schemas understandable to Flat File Pipeline components, such as Flat File Disassembler and Flat File Assembler.</span></span> <span data-ttu-id="99de5-104">您仍可使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 結構描述編輯器達成這個目的。</span><span class="sxs-lookup"><span data-stu-id="99de5-104">You can still do this using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Schema Editor.</span></span> <span data-ttu-id="99de5-105">若要減少手動步驟的次數以及建立方案所需的時間，您可使用 BizTalk 一般檔案結構描述精靈，此精靈提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="99de5-105">To reduce the number of manual steps and time needed to create solutions, you use the BizTalk Flat File Schema Wizard, which provides the following functionalities:</span></span>  
  
-   <span data-ttu-id="99de5-106">使用真正的一般檔案執行個體做為輸入。</span><span class="sxs-lookup"><span data-stu-id="99de5-106">Uses real flat file instances as input.</span></span>  
  
-   <span data-ttu-id="99de5-107">包含視覺化設計介面，可處理分隔和位置一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="99de5-107">Includes a visual design surface for working with delimited and positional flat file schemas.</span></span>  
  
-   <span data-ttu-id="99de5-108">使用可重新進入的精靈程序，可新增項目至結構描述和以互動方式定義一般檔案的相關註解。</span><span class="sxs-lookup"><span data-stu-id="99de5-108">Uses a re-entrant wizard-based process for adding elements to the schema and defining flat file related annotations interactively.</span></span>  
  
-   <span data-ttu-id="99de5-109">提供標記識別項和字元以及十六進位分隔符號的支援。</span><span class="sxs-lookup"><span data-stu-id="99de5-109">Provides support for tag identifiers and character and hexadecimal delimiters.</span></span>  
  
-   <span data-ttu-id="99de5-110">自動決定標記識別線偏移以及子分隔順序。</span><span class="sxs-lookup"><span data-stu-id="99de5-110">Automatically determines tag identifier offsets and child delimiting order.</span></span>  
  
-   <span data-ttu-id="99de5-111">提供檔案格式的預覽功能。</span><span class="sxs-lookup"><span data-stu-id="99de5-111">Provides preview capabilities for the file format.</span></span>  
  
-   <span data-ttu-id="99de5-112">可讓您在交換執行個體中選取要用來定義一般檔案結構描述的慣用子資料。</span><span class="sxs-lookup"><span data-stu-id="99de5-112">Enables you to select preferred sub-data within the interchange instance to use to define the flat file schemas.</span></span>  
  
## <a name="how-to-start-the-biztalk-flat-file-schema-wizard"></a><span data-ttu-id="99de5-113">如何啟動 BizTalk 一般檔案結構描述精靈</span><span class="sxs-lookup"><span data-stu-id="99de5-113">How to Start the BizTalk Flat File Schema Wizard</span></span>  
 <span data-ttu-id="99de5-114">您可從 Microsoft Visual Studio [方案總管] 或 BizTalk 結構描述編輯器啟動此精靈。</span><span class="sxs-lookup"><span data-stu-id="99de5-114">You can start the wizard from either the Microsoft Visual Studio Solution Explorer or from the BizTalk Schema Editor.</span></span>  
  
#### <a name="to-start-the-wizard-from-solution-explorer"></a><span data-ttu-id="99de5-115">從方案總管啟動此精靈</span><span class="sxs-lookup"><span data-stu-id="99de5-115">To start the wizard from Solution Explorer</span></span>  
  
1.  <span data-ttu-id="99de5-116">在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="99de5-116">In Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="99de5-117">若要加入新的一般檔案結構描述，以滑鼠右鍵按一下 BizTalk 專案，然後選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="99de5-117">To add the new flat-file schema, right-click the BizTalk project, and select **Add**.</span></span>  
  
3.  <span data-ttu-id="99de5-118">按一下**新項目。**</span><span class="sxs-lookup"><span data-stu-id="99de5-118">Click **New Item.**</span></span>  
  
     <span data-ttu-id="99de5-119">![方案總管功能表](../core/media/flatfileschemawizard-01.gif "FlatFileSchemaWizard_01")</span><span class="sxs-lookup"><span data-stu-id="99de5-119">![Solution Explorer menu](../core/media/flatfileschemawizard-01.gif "FlatFileSchemaWizard_01")</span></span>  
  
4.  <span data-ttu-id="99de5-120">在**加入新項目**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="99de5-120">In the **Add New Item** window, do the following:</span></span>  
  
    1.  <span data-ttu-id="99de5-121">在**類別**區段中，選取**結構描述檔案**。</span><span class="sxs-lookup"><span data-stu-id="99de5-121">In the **Categories** section, select **Schema Files**.</span></span>  
  
    2.  <span data-ttu-id="99de5-122">在**範本**區段中，選取**一般檔案結構描述精靈**。</span><span class="sxs-lookup"><span data-stu-id="99de5-122">In the **Templates** section, select **Flat File Schema Wizard**.</span></span>  
  
    3.  <span data-ttu-id="99de5-123">在**名稱** 文字方塊中，輸入新的結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="99de5-123">In the **Name** text box, type a name for the new schema.</span></span>  
  
    4.  <span data-ttu-id="99de5-124">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="99de5-124">Click **Add**.</span></span>  
  
         <span data-ttu-id="99de5-125">BizTalk 一般檔案結構描述精靈會開啟。</span><span class="sxs-lookup"><span data-stu-id="99de5-125">The BizTalk Flat File Schema Wizard opens.</span></span>  
  
#### <a name="to-start-the-wizard-from-the-schema-editor"></a><span data-ttu-id="99de5-126">從結構描述編輯器啟動此精靈</span><span class="sxs-lookup"><span data-stu-id="99de5-126">To start the Wizard from the Schema Editor</span></span>  
  
1.  <span data-ttu-id="99de5-127">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="99de5-127">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="99de5-128">若要加入新的一般檔案結構描述，以滑鼠右鍵按一下 BizTalk 專案，然後選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="99de5-128">To add the new flat-file schema, right-click the BizTalk project, and select **Add**.</span></span> <span data-ttu-id="99de5-129">選取**新項目**按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="99de5-129">Select **New Item** and click **New Item**.</span></span>  
  
3.  <span data-ttu-id="99de5-130">在**加入新項目**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="99de5-130">In the **Add New Item** window, do the following:</span></span>  
  
    1.  <span data-ttu-id="99de5-131">在**類別**區段中，選取**結構描述檔案**。</span><span class="sxs-lookup"><span data-stu-id="99de5-131">In the **Categories** section, select **Schema Files**.</span></span>  
  
    2.  <span data-ttu-id="99de5-132">在**範本**區段中，選取**一般檔案結構描述**。</span><span class="sxs-lookup"><span data-stu-id="99de5-132">In the **Templates** section, select **Flat File Schema**.</span></span>  
  
    3.  <span data-ttu-id="99de5-133">在**名稱** 文字方塊中，輸入新的結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="99de5-133">In the **Name** text box, type a name for the new schema.</span></span>  
  
    4.  <span data-ttu-id="99de5-134">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="99de5-134">Click **Add**.</span></span>  
  
    5.  <span data-ttu-id="99de5-135">以滑鼠右鍵按一下**根**選取**從一般檔案執行個體定義記錄**。</span><span class="sxs-lookup"><span data-stu-id="99de5-135">Right-click **Root** and select **Define Record from Flat File Instance**.</span></span>  
  
         <span data-ttu-id="99de5-136">BizTalk 一般檔案結構描述精靈現在會啟動。</span><span class="sxs-lookup"><span data-stu-id="99de5-136">The BizTalk Flat File Schema Wizard now starts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99de5-137">如果您有結構描述編輯器中開啟工作結構描述，您只需要為所選取的節點上按一下滑鼠右鍵，然後選取**從一般檔案執行個體定義記錄**。</span><span class="sxs-lookup"><span data-stu-id="99de5-137">If you have a working schema opened in the Schema Editor, all you need to do is right-click the selected node and then select **Define Record from Flat File Instance**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99de5-138">**從一般檔案執行個體定義記錄**選項已啟用選取的節點為不含子項目的記錄。</span><span class="sxs-lookup"><span data-stu-id="99de5-138">The **Define Record from Flat File Instance** option is enabled if the selected node is a record without child elements.</span></span> <span data-ttu-id="99de5-139">如果選取的節點包含子項目，此精靈就會刪除目前所有的子項目，然後產生新的子項目。</span><span class="sxs-lookup"><span data-stu-id="99de5-139">If the selected node has child elements, the wizard deletes all current child elements and generates the new ones.</span></span> <span data-ttu-id="99de5-140">在刪除現有的子項目之前，精靈會先提示您進行確認。</span><span class="sxs-lookup"><span data-stu-id="99de5-140">The wizard prompts you to confirm before deleting the existing child elements.</span></span>  
  
## <a name="considerations-for-using-the-flat-file-schema-wizard"></a><span data-ttu-id="99de5-141">使用一般檔案結構描述精靈的考量</span><span class="sxs-lookup"><span data-stu-id="99de5-141">Considerations for Using the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="99de5-142">此節描述在使用 BizTalk 一般檔案結構描述精靈時，您應考量的問題。</span><span class="sxs-lookup"><span data-stu-id="99de5-142">This section describes issues you should consider when working with the BizTalk Flat File Schema Wizard.</span></span>  
  
### <a name="working-with-multibyte-character-set-mbcs"></a><span data-ttu-id="99de5-143">使用多位元組字元集 (MBCS)</span><span class="sxs-lookup"><span data-stu-id="99de5-143">Working with Multibyte Character Set (MBCS)</span></span>  
 <span data-ttu-id="99de5-144">根據預設，**計算位置，以位元組為單位**核取方塊未選取 [一般檔案結構描述資訊] 畫面上。</span><span class="sxs-lookup"><span data-stu-id="99de5-144">By default, the **Count positions in bytes** check box is unchecked on the Flat File Schema Information screen.</span></span> <span data-ttu-id="99de5-145">精靈會以字元為單位計算位置；也就是說，如果在位置一般檔案執行個體中有 MBCS 字元，位置就無法被正確計算。</span><span class="sxs-lookup"><span data-stu-id="99de5-145">The wizard counts the positions by characters; which mean that if you have MBCS characters in your positional flat file instance, the positions are not counted correctly.</span></span> <span data-ttu-id="99de5-146">藉由選取**計算位置，以位元組為單位**核取方塊，精靈會顯示與其他表示其位置長度的 MBCS 字元。</span><span class="sxs-lookup"><span data-stu-id="99de5-146">By selecting the **Count positions in bytes** check box, the wizard displays MBCS characters with an additional indication of their positional length.</span></span> <span data-ttu-id="99de5-147">字元會顯示上的一個位置，以點號"•"填寫剩餘的長度。</span><span class="sxs-lookup"><span data-stu-id="99de5-147">The character takes one position on the display and the remaining length is filled out with dot symbols, “•”.</span></span> <span data-ttu-id="99de5-148">所填入的點號數量將取決於以雙位元組字元集 (DBCS)、Unicode 或 UTF-8 格式儲存的檔案。</span><span class="sxs-lookup"><span data-stu-id="99de5-148">The number of dot symbols filled will be depending on the files that were saved in double byte character set (DBCS), Unicode or UTF-8 format.</span></span>  
  
### <a name="code-pages-supported-in-the-flat-file-schema-wizard"></a><span data-ttu-id="99de5-149">一般檔案結構描述精靈中支援的字碼頁</span><span class="sxs-lookup"><span data-stu-id="99de5-149">Code Pages Supported in the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="99de5-150">以下是此精靈支援的字碼頁清單：</span><span class="sxs-lookup"><span data-stu-id="99de5-150">The following is a list of supported code pages for the wizard:</span></span>  
  
-   <span data-ttu-id="99de5-151">阿拉伯文 (1256)</span><span class="sxs-lookup"><span data-stu-id="99de5-151">Arabic (1256)</span></span>  
  
-   <span data-ttu-id="99de5-152">ASCII (20127)</span><span class="sxs-lookup"><span data-stu-id="99de5-152">ASCII (20127)</span></span>  
  
-   <span data-ttu-id="99de5-153">波羅的海文 (1257)</span><span class="sxs-lookup"><span data-stu-id="99de5-153">Baltic (1257)</span></span>  
  
-   <span data-ttu-id="99de5-154">Big-Endian-UTF16 (1201)</span><span class="sxs-lookup"><span data-stu-id="99de5-154">Big-Endian-UTF16 (1201)</span></span>  
  
-   <span data-ttu-id="99de5-155">中歐語系 (1250)</span><span class="sxs-lookup"><span data-stu-id="99de5-155">Central-European (1250)</span></span>  
  
-   <span data-ttu-id="99de5-156">斯拉夫文 (1251)</span><span class="sxs-lookup"><span data-stu-id="99de5-156">Cyrillic (1251)</span></span>  
  
-   <span data-ttu-id="99de5-157">希臘文 (1253)</span><span class="sxs-lookup"><span data-stu-id="99de5-157">Greek (1253)</span></span>  
  
-   <span data-ttu-id="99de5-158">希伯來文 (1255)</span><span class="sxs-lookup"><span data-stu-id="99de5-158">Hebrew (1255)</span></span>  
  
-   <span data-ttu-id="99de5-159">日文 (Shift-JIS) (932)</span><span class="sxs-lookup"><span data-stu-id="99de5-159">Japanese-Shift-JIS (932)</span></span>  
  
-   <span data-ttu-id="99de5-160">韓文 (949)</span><span class="sxs-lookup"><span data-stu-id="99de5-160">Korean (949)</span></span>  
  
-   <span data-ttu-id="99de5-161">Little-Endian-UTF16 (1200)</span><span class="sxs-lookup"><span data-stu-id="99de5-161">Little-Endian-UTF16 (1200)</span></span>  
  
-   <span data-ttu-id="99de5-162">簡體中文 (GBK) (936)</span><span class="sxs-lookup"><span data-stu-id="99de5-162">Simplified-Chinese-GBK (936)</span></span>  
  
-   <span data-ttu-id="99de5-163">簡體中文 (GB18030) (54936)</span><span class="sxs-lookup"><span data-stu-id="99de5-163">Simplified-Chinese-GB18030 (54936)</span></span>  
  
-   <span data-ttu-id="99de5-164">泰文 (874)</span><span class="sxs-lookup"><span data-stu-id="99de5-164">Thai (874)</span></span>  
  
-   <span data-ttu-id="99de5-165">繁體中文 (Big5) (950)</span><span class="sxs-lookup"><span data-stu-id="99de5-165">Traditional-Chinese-BIG5 (950)</span></span>  
  
-   <span data-ttu-id="99de5-166">土耳其文 (1254)</span><span class="sxs-lookup"><span data-stu-id="99de5-166">Turkish (1254)</span></span>  
  
-   <span data-ttu-id="99de5-167">UTF-7 (65000)</span><span class="sxs-lookup"><span data-stu-id="99de5-167">UTF-7 (65000)</span></span>  
  
-   <span data-ttu-id="99de5-168">UTF-8 (65001)</span><span class="sxs-lookup"><span data-stu-id="99de5-168">UTF-8 (65001)</span></span>  
  
-   <span data-ttu-id="99de5-169">越南文 (1258)</span><span class="sxs-lookup"><span data-stu-id="99de5-169">Vietnamese (1258)</span></span>  
  
-   <span data-ttu-id="99de5-170">西歐語系 (1252)</span><span class="sxs-lookup"><span data-stu-id="99de5-170">Western-European (1252)</span></span>  
  
### <a name="record-types-in-the-flat-file-schema-wizard"></a><span data-ttu-id="99de5-171">一般檔案結構描述精靈中的記錄類型</span><span class="sxs-lookup"><span data-stu-id="99de5-171">Record Types in the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="99de5-172">一般檔案在位置記錄中不可包含分隔記錄。</span><span class="sxs-lookup"><span data-stu-id="99de5-172">Flat files cannot contain delimited records within positional records.</span></span> <span data-ttu-id="99de5-173">由於精靈是可重新進入基礎，選項按鈕所定義的類型**依分隔符號**和**依相對位置**已啟用或停用的父記錄格式您在精靈中定義之子系。</span><span class="sxs-lookup"><span data-stu-id="99de5-173">Because the wizard is re-entrant based, the radio buttons that define the type of the **By delimiter symbol** and **By relative positions** are enabled or disabled based on the format of the parent records for the child which you define in the wizard.</span></span> <span data-ttu-id="99de5-174">例如，</span><span class="sxs-lookup"><span data-stu-id="99de5-174">For example,</span></span>  
  
-   <span data-ttu-id="99de5-175">如果精靈是對分隔記錄的子系執行，則兩個選項按鈕都會被選取。</span><span class="sxs-lookup"><span data-stu-id="99de5-175">If the wizard is run for a child of a delimited record, both radio buttons are selected.</span></span>  
  
-   <span data-ttu-id="99de5-176">如果您的子系位置記錄中，執行精靈**依分隔符號**清除選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="99de5-176">If the wizard is run for a child of a positional record, the **By delimiter symbol** radio button is cleared.</span></span>  
  
### <a name="delimiter-symbols-in-the-flat-file-schema-wizard"></a><span data-ttu-id="99de5-177">一般檔案結構描述精靈中的分隔符號</span><span class="sxs-lookup"><span data-stu-id="99de5-177">Delimiter Symbols in the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="99de5-178">子分隔符號屬性下拉式清單包含下列常見的分隔符號：</span><span class="sxs-lookup"><span data-stu-id="99de5-178">The child delimiter property drop-down list contains with the following common delimiters:</span></span>  
  
-   <span data-ttu-id="99de5-179">{CR}{LF}</span><span class="sxs-lookup"><span data-stu-id="99de5-179">{CR}{LF}</span></span>  
  
-   <span data-ttu-id="99de5-180">{CR}</span><span class="sxs-lookup"><span data-stu-id="99de5-180">{CR}</span></span>  
  
-   <span data-ttu-id="99de5-181">{LF}</span><span class="sxs-lookup"><span data-stu-id="99de5-181">{LF}</span></span>  
  
-   <span data-ttu-id="99de5-182">{TAB}</span><span class="sxs-lookup"><span data-stu-id="99de5-182">{TAB}</span></span>  
  
-   <span data-ttu-id="99de5-183">{SPACE}</span><span class="sxs-lookup"><span data-stu-id="99de5-183">{SPACE}</span></span>  
  
-   <span data-ttu-id="99de5-184">{0x1A}</span><span class="sxs-lookup"><span data-stu-id="99de5-184">{0x1A}</span></span>  
  
-   <span data-ttu-id="99de5-185">&#124;</span><span class="sxs-lookup"><span data-stu-id="99de5-185">&#124;</span></span>  
  
-   <span data-ttu-id="99de5-186">,</span><span class="sxs-lookup"><span data-stu-id="99de5-186">,</span></span>  
  
-   <span data-ttu-id="99de5-187">;</span><span class="sxs-lookup"><span data-stu-id="99de5-187">;</span></span>  
  
 <span data-ttu-id="99de5-188">此屬性的預設值為 {CR}{LF}。</span><span class="sxs-lookup"><span data-stu-id="99de5-188">The default value for this property is {CR}{LF}.</span></span> <span data-ttu-id="99de5-189">此屬性也是一個可編輯的文字方塊，可讓您指定子分隔符號做為字元序列或字元的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="99de5-189">The property is also an editable text box, so that you can specify the child delimiter as a sequence of characters or as hexadecimal values of the characters.</span></span> <span data-ttu-id="99de5-190">使用字元做為子分隔符號的範例包括 "a" 或 "street"。</span><span class="sxs-lookup"><span data-stu-id="99de5-190">An example of using characters for the child delimiter would be "a" or "street."</span></span> <span data-ttu-id="99de5-191">十六進位分隔符號使用下列格式指定：</span><span class="sxs-lookup"><span data-stu-id="99de5-191">Hexadecimal delimiters are specified using the following format:</span></span>  
  
-   <span data-ttu-id="99de5-192">{0xnnnn}。</span><span class="sxs-lookup"><span data-stu-id="99de5-192">{0xnnnn}.</span></span> <span data-ttu-id="99de5-193">例如，{0x0D}{0x0A}、{0x09} 或 {0x20}。</span><span class="sxs-lookup"><span data-stu-id="99de5-193">For example, {0x0D}{0x0A}, {0x09} or {0x20}.</span></span>  
  
 <span data-ttu-id="99de5-194">使用十六進位值序列的範例為 {0x0D}{0x0A}、{0x09}{0x20}。</span><span class="sxs-lookup"><span data-stu-id="99de5-194">An example of using sequence of hexadecimal values is {0x0D}{0x0A}, {0x09}{0x20}.</span></span>  
  
 <span data-ttu-id="99de5-195">如果您使用符號\\，{，或} 做為分隔符號，您必須取代分隔符號之前的額外反斜線符號，否則您會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="99de5-195">If you use the symbols \\, {, or } as the delimiter, you must place an additional backslash symbol in front of the delimiter symbol, otherwise you will receive an error message.</span></span> <span data-ttu-id="99de5-196">例如，</span><span class="sxs-lookup"><span data-stu-id="99de5-196">For example,</span></span>  
  
-   <span data-ttu-id="99de5-197">\\\\\\{，或\\}。</span><span class="sxs-lookup"><span data-stu-id="99de5-197">\\\\, \\{, or \\}.</span></span>  
  
### <a name="relative-positions-in-the-flat-file-schema-wizard"></a><span data-ttu-id="99de5-198">一般檔案結構描述精靈中的相對位置</span><span class="sxs-lookup"><span data-stu-id="99de5-198">Relative Positions in the Flat File Schema Wizard</span></span>  
  
#### <a name="setting-position-markers"></a><span data-ttu-id="99de5-199">設定位置標記</span><span class="sxs-lookup"><span data-stu-id="99de5-199">Setting Position Markers</span></span>  
 <span data-ttu-id="99de5-200">使用滑鼠左鍵按一下位置選取方塊，若要設定新的位置標記行中的位置標記。</span><span class="sxs-lookup"><span data-stu-id="99de5-200">Use the left mouse button to click a position marker in the position selection box to set the new position marker line.</span></span> <span data-ttu-id="99de5-201">位置標記會以實線表示。</span><span class="sxs-lookup"><span data-stu-id="99de5-201">The position marker is represented as a solid line.</span></span> <span data-ttu-id="99de5-202">依照預設，位置標記行是在位置零的記錄開頭。</span><span class="sxs-lookup"><span data-stu-id="99de5-202">By default, a position marker line exists at the beginning of the record at position zero.</span></span> <span data-ttu-id="99de5-203">若要移除現有的位置標記行，使用滑鼠左鍵按一下它。</span><span class="sxs-lookup"><span data-stu-id="99de5-203">To remove an existing position marker line, use the left mouse button to click  it.</span></span>  
  
### <a name="escape-characters-in-the-flat-file-schema-wizard"></a><span data-ttu-id="99de5-204">一般檔案結構描述精靈中的逸出字元</span><span class="sxs-lookup"><span data-stu-id="99de5-204">Escape Characters in the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="99de5-205">逸出字元是隱藏其後任何特殊意義字元的單一字元。</span><span class="sxs-lookup"><span data-stu-id="99de5-205">An escape character is a single character that suppresses any special meaning of the character that follows it.</span></span> <span data-ttu-id="99de5-206">如需詳細資訊，請參閱[逸出字元](../core/escape-characters.md)下的主題[方式解譯特殊字元做為欄位值的一部分](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)。</span><span class="sxs-lookup"><span data-stu-id="99de5-206">For more information, see [Escape Characters](../core/escape-characters.md) topic under [Ways to Interpret Special Characters as Part of a Field Value](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md).</span></span> <span data-ttu-id="99de5-207">您可在精靈中使用逸出字元，以指定在剖析一般檔案執行個體時要使用的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="99de5-207">You use the escape character property in the wizard to specify the escape character to use when parsing the flat file instance.</span></span> <span data-ttu-id="99de5-208">預設值為空值，表示會使用在結構描述層級所指定的預設逸出字元。</span><span class="sxs-lookup"><span data-stu-id="99de5-208">The default is null, meaning that the default escape character defined at the schema level is used.</span></span>  
  
 <span data-ttu-id="99de5-209">逸出字元可指定為字元或十六進位值。</span><span class="sxs-lookup"><span data-stu-id="99de5-209">The escape character can be specified as a character or as a hexadecimal value.</span></span> <span data-ttu-id="99de5-210">十六進位值使用下列格式指定：</span><span class="sxs-lookup"><span data-stu-id="99de5-210">The hexadecimal value is specified using the following format:</span></span>  
  
-   <span data-ttu-id="99de5-211">{0xnnnn}。</span><span class="sxs-lookup"><span data-stu-id="99de5-211">{0xnnnn}.</span></span> <span data-ttu-id="99de5-212">例如，{0x0D}{0x0A}、{0x09} 或 {0x20}。</span><span class="sxs-lookup"><span data-stu-id="99de5-212">For example, {0x0D}{0x0A}, {0x09}, or {0x20}.</span></span>  
  
 <span data-ttu-id="99de5-213">如果您使用符號\\，{，或} 做為逸出字元，您必須取代分隔符號之前的額外反斜線符號，否則您會收到錯誤訊息，例如</span><span class="sxs-lookup"><span data-stu-id="99de5-213">If you use the symbols \\, {, or } as the escape character, you must place an additional backslash symbol in front of the delimiter symbol, otherwise you will receive an error message For example,</span></span>  
  
-   <span data-ttu-id="99de5-214">\\\\, \\{, \\}.</span><span class="sxs-lookup"><span data-stu-id="99de5-214">\\\\, \\{, \\}.</span></span>  
  
### <a name="child-elements-in-the-flat-file-schema-wizard"></a><span data-ttu-id="99de5-215">一般檔案結構描述精靈中的子項目</span><span class="sxs-lookup"><span data-stu-id="99de5-215">Child Elements in the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="99de5-216">每個子項目包含**項目名稱**，**項目型別**，**資料型別**和**內容**。</span><span class="sxs-lookup"><span data-stu-id="99de5-216">Each child element contains **Element Name**, **Element Type**, **Data Type** and **Content**.</span></span> <span data-ttu-id="99de5-217">您使用**項目名稱**文字方塊中輸入節點的有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="99de5-217">You use the **Element Name** text box to type a meaningful name for the node.</span></span> <span data-ttu-id="99de5-218">**項目型別**是下拉式清單具有下列值：</span><span class="sxs-lookup"><span data-stu-id="99de5-218">The **Element Type** is a drop-down list with the following values:</span></span>  
  
-   <span data-ttu-id="99de5-219">**欄位項目**： 指定此節點會做為項目結構描述中建立。</span><span class="sxs-lookup"><span data-stu-id="99de5-219">**Field element**: Specifies that this node will be created in the schema as an element.</span></span>  
  
-   <span data-ttu-id="99de5-220">**欄位屬性**： 指定此節點會做為屬性結構描述中建立。</span><span class="sxs-lookup"><span data-stu-id="99de5-220">**Field attribute**: Specifies that this node will be created in the schema as an attribute.</span></span>  
  
-   <span data-ttu-id="99de5-221">**記錄**： 指定不含子系的記錄，將建立結構描述中。</span><span class="sxs-lookup"><span data-stu-id="99de5-221">**Record**: Specifies that a record without children will be created in the schema.</span></span>  
  
-   <span data-ttu-id="99de5-222">**重複記錄**： 指定不含子系的記錄將建立結構描述中，且其最大的項目設定為**Unbounded**。</span><span class="sxs-lookup"><span data-stu-id="99de5-222">**Repeating record**: Specifies that a record without children will be created in the schema and its max occurrence is set to **Unbounded**.</span></span>  
  
-   <span data-ttu-id="99de5-223">**忽略**： 不會建立這個節點的結構描述中。</span><span class="sxs-lookup"><span data-stu-id="99de5-223">**Ignore**: Nothing will be created in the schema for this node.</span></span>  
  
 <span data-ttu-id="99de5-224">根據預設所有項目屬於類型**欄位項目**而且其資料類型為**字串**。</span><span class="sxs-lookup"><span data-stu-id="99de5-224">By default all elements are of type **Field element** and their data type is **string**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99de5-225">子元素可以宣告為**欄位屬性**只有當沒有任何子系之前它會宣告為**欄位項目**，**記錄**或**重複記錄**。</span><span class="sxs-lookup"><span data-stu-id="99de5-225">A child element can be declared as a **Field attribute** only if there are no children before it that are declared as **Field elements**, **Record** or **Repeating record**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99de5-226">您會看到驚嘆號前面**子節點**在下列情況：</span><span class="sxs-lookup"><span data-stu-id="99de5-226">You will see an exclamation mark in front of the **child nodes** in the following instances:</span></span>  
  
-   <span data-ttu-id="99de5-227">**欄位屬性**之後**欄位項目**，**記錄，**或**重複記錄**。</span><span class="sxs-lookup"><span data-stu-id="99de5-227">The **Field attribute** is defined after **Field element**, **Record,** or **Repeating record**.</span></span>  
  
-   <span data-ttu-id="99de5-228">此子項目沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="99de5-228">The child element does not have a name.</span></span>  
  
-   <span data-ttu-id="99de5-229">此子項目有重複的名稱。</span><span class="sxs-lookup"><span data-stu-id="99de5-229">The child element has a duplicate name.</span></span>  
  
-   <span data-ttu-id="99de5-230">子項目的選定資料類型不適合內容。</span><span class="sxs-lookup"><span data-stu-id="99de5-230">The selected data type for the child element is not suitable for the content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99de5-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99de5-231">See Also</span></span>  
 [<span data-ttu-id="99de5-232">BizTalk 一般檔案結構描述精靈逐步解說</span><span class="sxs-lookup"><span data-stu-id="99de5-232">BizTalk Flat File Schema Wizard Walkthrough</span></span>](../core/biztalk-flat-file-schema-wizard-walkthrough.md)