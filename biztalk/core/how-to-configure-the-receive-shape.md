---
title: 如何設定 「 接收 」 圖形 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filter expressions, Receive shape [Orchestration Designer]
- Receive shape [Orchestration Designer], about Receive shape
- configuring [Orchestration Designer], Receive shapes
- Receive shape [Orchestration Designer]
- Receive shape [Orchestration Designer], filter expressions
ms.assetid: 15aadee4-fa05-4edd-a191-e4d191c1ea22
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60d2a0913e6921b5868a16c58c7ed2c7ae3d46e4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989703"
---
# <a name="how-to-configure-the-receive-shape"></a><span data-ttu-id="3ad24-102">如何設定接收圖形</span><span class="sxs-lookup"><span data-stu-id="3ad24-102">How to Configure the Receive Shape</span></span>
<span data-ttu-id="3ad24-103">![](../core/media/ebiz-orch-receive.gif "ebiz_orch_receive")</span><span class="sxs-lookup"><span data-stu-id="3ad24-103">![](../core/media/ebiz-orch-receive.gif "ebiz_orch_receive")</span></span>  
<span data-ttu-id="3ad24-104">接收圖形</span><span class="sxs-lookup"><span data-stu-id="3ad24-104">Receive shape</span></span>  

 <span data-ttu-id="3ad24-105">A**接收**圖形可以用來啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="3ad24-105">A **Receive** shape can be used to start an orchestration.</span></span> <span data-ttu-id="3ad24-106">如果您設定**Activate**屬性設 **，則為 True**，執行階段引擎會測試內送訊息以查看它是否屬於正確的類型以及如果套用的篩選，是否在篩選條件運算式滿足。</span><span class="sxs-lookup"><span data-stu-id="3ad24-106">If you set the **Activate** property to **True**, the runtime engine will test an incoming message to see whether it is of the right type and, if a filter has been applied, whether the filter expression is satisfied.</span></span> <span data-ttu-id="3ad24-107">如果符合接收訊息的準則，在執行階段引擎會建立並執行新的協調流程執行個體，而**接收**圖形接收訊息。</span><span class="sxs-lookup"><span data-stu-id="3ad24-107">If the criteria for receipt of the message are met, the runtime engine creates and runs a new orchestration instance, and the **Receive** shape receives the message.</span></span>  

> [!NOTE]
>  <span data-ttu-id="3ad24-108">如果**Activate**的 「 接收 」 圖形的屬性設定為 True，**接收**必須在協調流程中的第一個動作。</span><span class="sxs-lookup"><span data-stu-id="3ad24-108">If the **Activate** property of a Receive shape is set to True, the **Receive** must be the first action in the orchestration.</span></span>  

> [!NOTE]
>  <span data-ttu-id="3ad24-109">如果**Activate**屬性設定為 False，所有**接收**圖形，您的協調流程必須由呼叫另一個協調流程才能執行。</span><span class="sxs-lookup"><span data-stu-id="3ad24-109">If the **Activate** property is set to False on all **Receive** shapes, your orchestration must be called by another orchestration in order to run.</span></span>  

> [!NOTE]
>  <span data-ttu-id="3ad24-110">如果您將放**接收**範圍內的圖形**Activate**屬性設定為 **，則為 True**，而不需要變更，然後將.NET 類別變數新增至您的協調流程變數的**使用預設建構函式**屬性設**False**，則啟動接收陳述式會產生的 XLANG/S 程式碼，在範圍外，但仍會繼續在設計介面顯示為在範圍內。</span><span class="sxs-lookup"><span data-stu-id="3ad24-110">If you put a **Receive** shape inside a scope with the **Activate** property set to **True**, and then add a .NET Class variable to your orchestration without changing the variable's **Use Default Constructor** property to **False**, the activate receive statement will be outside of the scope in the generated XLANG/S code, but the design surface will continue to show it as being inside the scope.</span></span>  

 <span data-ttu-id="3ad24-111">每個協調流程必須至少一個**接收**圖形**Activate**屬性設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="3ad24-111">Each orchestration must have at least one **Receive** shape with the **Activate** property set to **True**.</span></span>  

 <span data-ttu-id="3ad24-112">若您預期收到您已送出之訊息的間接或非同步回應 (不使用要求-回應連接埠)，則需要將訊息與目前正在執行的協調流程執行個體建立相互關聯，讓回應者能將回應送給正確的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ad24-112">If you expect to receive an indirect or asynchronous response (not on a request-response port) to a message that you have previously sent, you need to correlate the message with the currently running instance of the orchestration, so that the respondent can get the response to the correct instance.</span></span> <span data-ttu-id="3ad24-113">您可以套用初始化的相互關聯，如果您打算執行後續的相互關聯，內送訊息中的值設定為 「 接收 」 圖形或以下的相互關聯集合相互關聯使用先前初始化的相互關聯集。</span><span class="sxs-lookup"><span data-stu-id="3ad24-113">You can apply an initializing correlation set to the Receive shape if you plan to do subsequent correlation on values in the incoming message, or a following correlation set for correlating using a previously initialized correlation set.</span></span> <span data-ttu-id="3ad24-114">如需詳細資訊，請參閱 <<c0> [ 協調流程中使用的相互關聯](../core/using-correlations-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="3ad24-114">For more information, see [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md).</span></span>  

### <a name="to-configure-a-receive-shape"></a><span data-ttu-id="3ad24-115">設定接收圖形</span><span class="sxs-lookup"><span data-stu-id="3ad24-115">To configure a Receive shape</span></span>  

1.  <span data-ttu-id="3ad24-116">設定訊息和連接埠作業。</span><span class="sxs-lookup"><span data-stu-id="3ad24-116">Set a message and a port operation.</span></span>  

    1.  <span data-ttu-id="3ad24-117">在 [協調流程檢視] 視窗中，確認您的協調流程已經為接收的訊息類型，定義訊息和連接埠作業。</span><span class="sxs-lookup"><span data-stu-id="3ad24-117">In the Orchestration View window, verify that your orchestration has both a message and a port operation defined for the message type being received.</span></span>  

         <span data-ttu-id="3ad24-118">在 屬性 視窗中，選取 從接收訊息**訊息**屬性下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="3ad24-118">In the Properties window, select the message to receive from the **Message** property drop-down list.</span></span>  

    2.  <span data-ttu-id="3ad24-119">在 屬性 視窗中，選取 連接埠作業，以接收來自訊息**作業**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="3ad24-119">In the Properties window, select the port operation to receive the message from the **Operation** drop-down list.</span></span>  

         <span data-ttu-id="3ad24-120">-或-</span><span class="sxs-lookup"><span data-stu-id="3ad24-120">—Or—</span></span>  

         <span data-ttu-id="3ad24-121">從接收連接器拖曳到**接收**圖形以將接收的訊息的連接埠通訊端。</span><span class="sxs-lookup"><span data-stu-id="3ad24-121">Drag the receive connector from the **Receive** shape to the port socket that will receive the message.</span></span>  

2.  <span data-ttu-id="3ad24-122">指定**接收**圖形啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="3ad24-122">Specify that the **Receive** shape will activate the orchestration.</span></span>  

3.  <span data-ttu-id="3ad24-123">在 [屬性] 視窗中，將 [啟動] 屬性設定為 True。</span><span class="sxs-lookup"><span data-stu-id="3ad24-123">In the Properties window, set the Activate property to True.</span></span>  

    1.  <span data-ttu-id="3ad24-124">在 [屬性] 視窗中，按一下**省略符號**(**...**) 按鈕來建立篩選器，以限制的訊息篩選條件運算式屬性的這個**接收**圖形接受。</span><span class="sxs-lookup"><span data-stu-id="3ad24-124">In the Properties window, click the **Ellipsis** (**...**) button for the Filter Expression property to create a filter to restrict the messages that this **Receive** shape accepts.</span></span>  

         <span data-ttu-id="3ad24-125">-或-</span><span class="sxs-lookup"><span data-stu-id="3ad24-125">—Or—</span></span>  

         <span data-ttu-id="3ad24-126">以滑鼠右鍵按一下**接收**圖形，然後按一下**編輯篩選條件運算式**。</span><span class="sxs-lookup"><span data-stu-id="3ad24-126">Right-click the **Receive** shape and then click **Edit Filter Expression**.</span></span>  

    2.  <span data-ttu-id="3ad24-127">**篩選條件運算式** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3ad24-127">The **Filter Expression** dialog box appears.</span></span> <span data-ttu-id="3ad24-128">使用此對話方塊來建立一或多個篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="3ad24-128">Use this dialog box to create one or more filter expressions.</span></span>  

        > [!NOTE]
        >  <span data-ttu-id="3ad24-129">必須定義訊息類型，並指派給**接收**圖形之前，您可以將篩選套用至它。</span><span class="sxs-lookup"><span data-stu-id="3ad24-129">A message type must be defined and assigned to the **Receive** shape before you can apply a filter to it.</span></span>  

4.  <span data-ttu-id="3ad24-130">指定相互關聯集來限制的訊息**接收**圖形接受。</span><span class="sxs-lookup"><span data-stu-id="3ad24-130">Specify correlation sets to restrict the messages the **Receive** shape accepts.</span></span>  

    -   <span data-ttu-id="3ad24-131">針對您想要遵循每個相互關聯集，檢查相互關聯集從下拉式清單上**沿用相互關聯集**屬性。</span><span class="sxs-lookup"><span data-stu-id="3ad24-131">For each correlation set you want to follow, check a correlation set from the drop-down on the **Following Correlation Sets** property.</span></span>  

    -   <span data-ttu-id="3ad24-132">用於每個相互關聯集您想要初始化，請檢查相互關聯集從下拉式清單上**初始相互關聯集**屬性。</span><span class="sxs-lookup"><span data-stu-id="3ad24-132">For each correlation set that you want to initialize, check a correlation set from the drop-down on the **Initializing Correlation Sets** property.</span></span>  

## <a name="filter-expression-grid-control"></a><span data-ttu-id="3ad24-133">篩選條件運算式格線控制項</span><span class="sxs-lookup"><span data-stu-id="3ad24-133">Filter Expression grid control</span></span>  
 <span data-ttu-id="3ad24-134">您可以使用此格線控制項定義構成運算式的述詞，以建置篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="3ad24-134">You build a filter expression by using this grid control to define the predicates that make up the expression.</span></span> <span data-ttu-id="3ad24-135">您可以在格線的儲存格中新增、編輯和刪除述詞。</span><span class="sxs-lookup"><span data-stu-id="3ad24-135">You can add, edit, and delete predicates from the cells of the grid.</span></span> <span data-ttu-id="3ad24-136">此格線控制項有四個資料行： 屬性、 運算子、 值和群組。</span><span class="sxs-lookup"><span data-stu-id="3ad24-136">This grid control has four columns: Property, Operator, Value, and Grouping.</span></span>  

- <span data-ttu-id="3ad24-137">**屬性。**</span><span class="sxs-lookup"><span data-stu-id="3ad24-137">**Property.**</span></span> <span data-ttu-id="3ad24-138">您可以輸入屬性參考，或從儲存格的下拉式清單中選取一個屬性。</span><span class="sxs-lookup"><span data-stu-id="3ad24-138">You can type a property reference, or select one from the cell's drop-down list.</span></span> <span data-ttu-id="3ad24-139">該清單包含內送訊息的屬性。</span><span class="sxs-lookup"><span data-stu-id="3ad24-139">The list contains properties on the incoming message.</span></span>  

- <span data-ttu-id="3ad24-140">**運算子。**</span><span class="sxs-lookup"><span data-stu-id="3ad24-140">**Operator.**</span></span> <span data-ttu-id="3ad24-141">您可以在此儲存格輸入運算子，或從下拉式清單中選取運算子。</span><span class="sxs-lookup"><span data-stu-id="3ad24-141">You can type in this cell, or select an operator from the drop-down list.</span></span> <span data-ttu-id="3ad24-142">可能的選項為：</span><span class="sxs-lookup"><span data-stu-id="3ad24-142">Possible selections are:</span></span>  


  | <span data-ttu-id="3ad24-143">運算元</span><span class="sxs-lookup"><span data-stu-id="3ad24-143">Operand</span></span> |           <span data-ttu-id="3ad24-144">意義</span><span class="sxs-lookup"><span data-stu-id="3ad24-144">Meaning</span></span>           |
  |---------|-----------------------------|
  |   ==    |         <span data-ttu-id="3ad24-145">等於</span><span class="sxs-lookup"><span data-stu-id="3ad24-145">Is equal to</span></span>         |
  |   <span data-ttu-id="3ad24-146">!=</span><span class="sxs-lookup"><span data-stu-id="3ad24-146">!=</span></span>    |       <span data-ttu-id="3ad24-147">不等於</span><span class="sxs-lookup"><span data-stu-id="3ad24-147">Is not equal to</span></span>       |
  |    <    |        <span data-ttu-id="3ad24-148">小於</span><span class="sxs-lookup"><span data-stu-id="3ad24-148">Is less than</span></span>         |
  |   \<=   |  <span data-ttu-id="3ad24-149">小於或等於</span><span class="sxs-lookup"><span data-stu-id="3ad24-149">Is less than or equal to</span></span>   |
  |    >    |       <span data-ttu-id="3ad24-150">大於</span><span class="sxs-lookup"><span data-stu-id="3ad24-150">Is greater than</span></span>       |
  |   \>=   | <span data-ttu-id="3ad24-151">大於或等於</span><span class="sxs-lookup"><span data-stu-id="3ad24-151">Is greater than or equal to</span></span> |
  | <span data-ttu-id="3ad24-152">Exists</span><span class="sxs-lookup"><span data-stu-id="3ad24-152">Exists</span></span>  |           <span data-ttu-id="3ad24-153">Exists</span><span class="sxs-lookup"><span data-stu-id="3ad24-153">Exists</span></span>            |


- <span data-ttu-id="3ad24-154">**值。**</span><span class="sxs-lookup"><span data-stu-id="3ad24-154">**Value.**</span></span> <span data-ttu-id="3ad24-155">中的儲存格**值**資料行可以保存您在中輸入任何常數： 字串常值、 整數常值或 null。</span><span class="sxs-lookup"><span data-stu-id="3ad24-155">Cells in the **Value** column can hold any constant that you type in: a string-literal, an integer-literal, or null.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="3ad24-156">如果所選取屬性的類型為字串，該值必須在引號中。</span><span class="sxs-lookup"><span data-stu-id="3ad24-156">If the property selected is of type string, the value needs to be in quotes.</span></span> <span data-ttu-id="3ad24-157">例如，SMTP.From = "MyServer"。</span><span class="sxs-lookup"><span data-stu-id="3ad24-157">For example, SMTP.From = "MyServer".</span></span>  

- <span data-ttu-id="3ad24-158">**群組。**</span><span class="sxs-lookup"><span data-stu-id="3ad24-158">**Grouping.**</span></span> <span data-ttu-id="3ad24-159">您可以使用此欄來控制述詞群組。</span><span class="sxs-lookup"><span data-stu-id="3ad24-159">Use this column to control predicate grouping.</span></span> <span data-ttu-id="3ad24-160">篩選條件運算式一律以 DNF (Disjunctive Normal Form) 來表示，以便自動決定群組。</span><span class="sxs-lookup"><span data-stu-id="3ad24-160">Filter expressions are always expressed in Disjunctive Normal Form (DNF) so grouping can be determined automatically.</span></span> <span data-ttu-id="3ad24-161">[AND] 表示將述詞和其後的述詞群組起來，而 [OR] 表示述詞和下一列的述詞是分開的。</span><span class="sxs-lookup"><span data-stu-id="3ad24-161">AND means the predicate is to be grouped with the predicate following it, while OR means the predicate is separate from the predicate in the next row.</span></span> <span data-ttu-id="3ad24-162">當述詞組成群組時，格線控制項左邊會出現灰色中括弧。</span><span class="sxs-lookup"><span data-stu-id="3ad24-162">Gray brackets to the left of the grid control appear when predicates are grouped together.</span></span> <span data-ttu-id="3ad24-163">述詞無法組成巢狀群組。</span><span class="sxs-lookup"><span data-stu-id="3ad24-163">Predicate groups cannot be nested.</span></span> <span data-ttu-id="3ad24-164">若未在此儲存格中指定值，儲存格的預設值為 AND。</span><span class="sxs-lookup"><span data-stu-id="3ad24-164">If you do not specify a value in this cell, the value of the cell defaults to AND.</span></span>  

  <span data-ttu-id="3ad24-165">例如，您可能建立如下的運算式：</span><span class="sxs-lookup"><span data-stu-id="3ad24-165">For example, you might create an expression like the following:</span></span>  

  `MSMQ.MsgID = 1`  

  <span data-ttu-id="3ad24-166">依照這個篩選條件，傳送埠群組將只能訂閱 MSMQ 訊息識別碼為 1 的訊息。</span><span class="sxs-lookup"><span data-stu-id="3ad24-166">With this filter, the send port group would only subscribe to messages having an MSMQ message ID of 1.</span></span>  

  <span data-ttu-id="3ad24-167">您可以建立額外的運算式，並指定這些運算式與其他運算式之間有 AND 或 OR 關係，例如：</span><span class="sxs-lookup"><span data-stu-id="3ad24-167">You can create additional expressions and specify that they have an AND or OR relationship with other expressions, for example:</span></span>  

  `MSMQ.MsgID = 1 OR`  

  `SMTP.From = "MyServer"`  

  <span data-ttu-id="3ad24-168">在此例中，傳送埠群組將會訂閱 MSMQ 訊息識別碼為 1 的或從名為 MyServer 的 SMTP 伺服器所傳送的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="3ad24-168">In this case, the send port group would subscribe to all messages that have either an MSMQ message ID of 1 or that have been sent from the SMTP server named MyServer.</span></span>  

## <a name="hint-label"></a><span data-ttu-id="3ad24-169">提示標籤</span><span class="sxs-lookup"><span data-stu-id="3ad24-169">Hint label</span></span>  
 <span data-ttu-id="3ad24-170">此欄位會指引使用者。</span><span class="sxs-lookup"><span data-stu-id="3ad24-170">This field provides user guidance.</span></span> <span data-ttu-id="3ad24-171">標籤文字會隨著包含作用中儲存格的資料行改變。</span><span class="sxs-lookup"><span data-stu-id="3ad24-171">The label text changes depending on which column contains the active cell.</span></span> <span data-ttu-id="3ad24-172">此文字會顯示資料行名稱，後面接著引導文字，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3ad24-172">The text displays the column name followed by guidance text as follows:</span></span>  

-   <span data-ttu-id="3ad24-173">**屬性。**</span><span class="sxs-lookup"><span data-stu-id="3ad24-173">**Property.**</span></span> <span data-ttu-id="3ad24-174">請從清單選取內送訊息上的屬性。</span><span class="sxs-lookup"><span data-stu-id="3ad24-174">Please select a property on the incoming message from the list.</span></span>  

-   <span data-ttu-id="3ad24-175">**運算子。**</span><span class="sxs-lookup"><span data-stu-id="3ad24-175">**Operator.**</span></span> <span data-ttu-id="3ad24-176">選取運算子，以進行 [屬性] 與 [值] 的比較。</span><span class="sxs-lookup"><span data-stu-id="3ad24-176">Select an operator to compare the Property with the Value.</span></span>  

-   <span data-ttu-id="3ad24-177">**值。**</span><span class="sxs-lookup"><span data-stu-id="3ad24-177">**Value.**</span></span> <span data-ttu-id="3ad24-178">從清單選取訊息屬性，或輸入常值。</span><span class="sxs-lookup"><span data-stu-id="3ad24-178">Select a message property from the list, or type in a literal value.</span></span>  

-   <span data-ttu-id="3ad24-179">**群組。**</span><span class="sxs-lookup"><span data-stu-id="3ad24-179">**Grouping.**</span></span> <span data-ttu-id="3ad24-180">指定此列如何與下一列群組在一起。</span><span class="sxs-lookup"><span data-stu-id="3ad24-180">Specify how this row is to be grouped with the next row.</span></span> <span data-ttu-id="3ad24-181">'AND' 將會聯結資料列，而 'OR' 會分開它們。</span><span class="sxs-lookup"><span data-stu-id="3ad24-181">'AND' will join the rows, and 'OR' will separate them.</span></span>  

## <a name="move-up-button"></a><span data-ttu-id="3ad24-182">上移按鈕</span><span class="sxs-lookup"><span data-stu-id="3ad24-182">Move Up button</span></span>  
 <span data-ttu-id="3ad24-183">按一下此按鈕，將選取的列上移</span><span class="sxs-lookup"><span data-stu-id="3ad24-183">Click this to move a selected row up.</span></span> <span data-ttu-id="3ad24-184">(第一次，即可選取資料列*向右箭號*(**>)** ，格線控制項左邊的按鈕。)</span><span class="sxs-lookup"><span data-stu-id="3ad24-184">(First select a row by clicking the *right arrow* (**>)** button at the left side of the grid control.)</span></span>  

## <a name="move-down-button"></a><span data-ttu-id="3ad24-185">下移按鈕</span><span class="sxs-lookup"><span data-stu-id="3ad24-185">Move Down button</span></span>  
 <span data-ttu-id="3ad24-186">按一下此按鈕，將選取的列下移</span><span class="sxs-lookup"><span data-stu-id="3ad24-186">Click this to move a selected row down.</span></span> <span data-ttu-id="3ad24-187">(第一次，即可選取資料列*向右箭號*(**>)** ，格線控制項左邊的按鈕。)</span><span class="sxs-lookup"><span data-stu-id="3ad24-187">(First select a row by clicking the *right arrow* (**>)** button at the left side of the grid control.)</span></span>  

## <a name="filter-expression-created-field"></a><span data-ttu-id="3ad24-188">建立的篩選條件運算式欄位</span><span class="sxs-lookup"><span data-stu-id="3ad24-188">Filter Expression Created field</span></span>  
 <span data-ttu-id="3ad24-189">這個唯讀文字方塊會在您建立運算式時顯示它。</span><span class="sxs-lookup"><span data-stu-id="3ad24-189">This read-only text box shows the expression as you are building it.</span></span>  

## <a name="in-this-section"></a><span data-ttu-id="3ad24-190">本節內容</span><span class="sxs-lookup"><span data-stu-id="3ad24-190">In This Section</span></span>  
 [<span data-ttu-id="3ad24-191">搭配使用篩選與接收訊息圖形</span><span class="sxs-lookup"><span data-stu-id="3ad24-191">Using Filters With the Receive Message Shape</span></span>](../core/using-filters-with-the-receive-message-shape.md)