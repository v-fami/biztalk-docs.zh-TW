---
title: 如何新增協調流程變數 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, variables
ms.assetid: c387cd56-5443-4de2-bbda-be34b95cbe71
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb8516ceb780e64c4f4a01370de0e7c40098f3da
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968828"
---
# <a name="how-to-add-orchestration-variables"></a><span data-ttu-id="5977d-102">如何新增協調流程變數</span><span class="sxs-lookup"><span data-stu-id="5977d-102">How to Add Orchestration Variables</span></span>
<span data-ttu-id="5977d-103">[協調流程檢視] 視窗可讓您管理協調流程的屬性 (也稱為**服務**屬性)、 參數、 連接埠、 訊息，以及其他變數。</span><span class="sxs-lookup"><span data-stu-id="5977d-103">The Orchestration View window enables you to manage an orchestration's properties (also known as **Service** properties), parameters, ports, messages, and other variables.</span></span> <span data-ttu-id="5977d-104">除了連接埠和訊息之外，您還可以建立整數變數、布林值變數、字串變數或 .NET 類別的變數。</span><span class="sxs-lookup"><span data-stu-id="5977d-104">In addition to ports and messages, you can create integer variables, Boolean variables, string variables, or variables of a .NET class.</span></span>  
  
 <span data-ttu-id="5977d-105">您也可以使用 [協調流程檢視] 視窗來管理屬於您範圍的變數。</span><span class="sxs-lookup"><span data-stu-id="5977d-105">You can also use the Orchestration View window to manage the variables that belong to your scopes.</span></span>  
  
### <a name="to-add-a-variable"></a><span data-ttu-id="5977d-106">加入變數</span><span class="sxs-lookup"><span data-stu-id="5977d-106">To add a variable</span></span>  
  
1.  <span data-ttu-id="5977d-107">在協調流程檢視 視窗中，以滑鼠右鍵按一下**變數**資料夾，然後按一下**新變數**。</span><span class="sxs-lookup"><span data-stu-id="5977d-107">In the Orchestration View window, right-click the **Variables** folder and then click **New Variable**.</span></span>  
  
     <span data-ttu-id="5977d-108">**變數**資料夾，則會展開摺疊，並加入新的變數。</span><span class="sxs-lookup"><span data-stu-id="5977d-108">The **Variables** folder expands, if collapsed, and a new variable is added.</span></span>  
  
2.  <span data-ttu-id="5977d-109">在 [屬性] 視窗的 [識別項] 屬性中輸入名稱，為變數命名。</span><span class="sxs-lookup"><span data-stu-id="5977d-109">Name the variable by typing a name in the Identifier property in the Properties window.</span></span>  
  
3.  <span data-ttu-id="5977d-110">讓變數和類型 (例如 .NET 類別) 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="5977d-110">Associate the variable with a type, such as a .NET class.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5977d-111">**類型**下拉式清單包含下列預先定義的變數類型：**布林**，**位元組**， **datetime**， **十進位**， **double**， **int16**， **int32**， **int64**， **sbyte\*\*\*\*單一**，**字串**， **timespan**， **uint16**， **uint32**，和**uint64**。</span><span class="sxs-lookup"><span data-stu-id="5977d-111">The **Types** drop-down list contains the following predefined variable types: **boolean**, **byte**, **datetime**, **decimal**, **double**, **int16**, **int32**, **int64**, **sbyte**, **single**, **string**, **timespan**, **uint16**, **uint32**, and **uint64**.</span></span> <span data-ttu-id="5977d-112">您也可以存取.NET 資料型別和類別，藉由選取**\<.NET 類別...\>**，它會啟動**選取成品類型** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5977d-112">You can also access .NET data types and classes by selecting **\<.NET Class...\>**, which brings up the **Select Artifact Type** dialog box.</span></span>  
  
4.  <span data-ttu-id="5977d-113">如果您選取預先定義的變數類型，就可以選擇指定變數的初始值。</span><span class="sxs-lookup"><span data-stu-id="5977d-113">If you select a predefined variable type, you have the option of specifying an initial value for the variable.</span></span> <span data-ttu-id="5977d-114">在 [屬性] 視窗中，設定**初始值**屬性。</span><span class="sxs-lookup"><span data-stu-id="5977d-114">In the Properties window, set the **Initial Value** property.</span></span>  
  
     <span data-ttu-id="5977d-115">若選取的類型是 .NET 類別，您可以選擇使用預設的建構函式。</span><span class="sxs-lookup"><span data-stu-id="5977d-115">Otherwise, if the selected type is a .NET class, you have the option of using a default constructor.</span></span> <span data-ttu-id="5977d-116">在 [屬性] 視窗中，設定以下屬性：</span><span class="sxs-lookup"><span data-stu-id="5977d-116">In the Properties window, set the following property:</span></span>  
  
    |<span data-ttu-id="5977d-117">屬性</span><span class="sxs-lookup"><span data-stu-id="5977d-117">Property</span></span>|<span data-ttu-id="5977d-118">Description</span><span class="sxs-lookup"><span data-stu-id="5977d-118">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="5977d-119">**使用預設建構函式**</span><span class="sxs-lookup"><span data-stu-id="5977d-119">**Use Default Constructor**</span></span>|<span data-ttu-id="5977d-120">若 .NET 類別可以使用預設建構函式，此屬性會決定當您第一次使用變數時，是否要呼叫預設的建構函式：</span><span class="sxs-lookup"><span data-stu-id="5977d-120">If a default constructor is available for a .NET class, this property determines whether the default constructor will be called when you use the variable for the first time:</span></span><br /><br /> <span data-ttu-id="5977d-121">True：將呼叫預設的建構函式。</span><span class="sxs-lookup"><span data-stu-id="5977d-121">True—The default constructor will be called.</span></span> <span data-ttu-id="5977d-122">這是在有預設建構函式可供使用時的預設值。</span><span class="sxs-lookup"><span data-stu-id="5977d-122">This is the default value when a default constructor is available.</span></span><br /><br /> <span data-ttu-id="5977d-123">False：不會呼叫預設建構函式。您必須在運算式中呼叫建構函式，或將它指派給變數，才能在您的協調流程中使用該建構函式。</span><span class="sxs-lookup"><span data-stu-id="5977d-123">False—The default constructor will not be called; you must call a constructor in an expression or make an assignment to the variable before you can use it in your orchestration.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="5977d-124">如果預設建構函式需要輸入的參數，您可以設定**使用預設建構函式**至**False** ，然後呼叫建構函式從**指派**圖形; 針對範例中， `myVariable = myNamespace.myClass (param1, param2)`。</span><span class="sxs-lookup"><span data-stu-id="5977d-124">If the default constructor requires input parameters, you can set **Use Default Constructor** to **False** and then call the constructor from an **Assignment** shape; for example, `myVariable = myNamespace.myClass (param1, param2)`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5977d-125">當您將變數新增至協調流程時，在完整定義之前，您會在協調流程中看到驚嘆號。</span><span class="sxs-lookup"><span data-stu-id="5977d-125">When you add a variable to the orchestration, before it is fully defined, you will see exclamation marks in the orchestration.</span></span> <span data-ttu-id="5977d-126">如果您在完整定義之前且驚嘆號仍然出現在協調流程中時刪除這個變數，就可以建立後再刪除協調流程參數，以強制讓協調流程移除這些驚嘆號。</span><span class="sxs-lookup"><span data-stu-id="5977d-126">If you delete this variable before it is fully defined and the exclamation marks still appear in the orchestration, you can force the orchestration to remove these exclamation marks by creating and then deleting an orchestration parameter.</span></span>  
  
### <a name="to-remove-a-variable"></a><span data-ttu-id="5977d-127">移除變數</span><span class="sxs-lookup"><span data-stu-id="5977d-127">To remove a variable</span></span>  
  
-   <span data-ttu-id="5977d-128">在協調流程檢視] 視窗中，以滑鼠右鍵按一下您想要移除，然後按一下 [的變數**刪除**。</span><span class="sxs-lookup"><span data-stu-id="5977d-128">In the Orchestration View window, right-click the variable you want to remove and then click **Delete**.</span></span>