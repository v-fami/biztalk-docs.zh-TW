---
title: HL7 加速器，BizTalk Server 中的詞彙 |Microsoft Docs
description: 一般詞彙和定義了解，並了解如何使用 BizTalk Accelerator for HL7
ms.custom: ''
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ffb9c18a-5fe5-448f-b115-0973e9d12952
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b632f494766974079ec13dd0803ae776c96adfe2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997879"
---
# <a name="glossary"></a><span data-ttu-id="b1084-103">詞彙</span><span class="sxs-lookup"><span data-stu-id="b1084-103">Glossary</span></span>
<span data-ttu-id="b1084-104">Microsoft BizTalk Accelerator for HL7 會使用下列詞彙和定義。</span><span class="sxs-lookup"><span data-stu-id="b1084-104">Microsoft BizTalk Accelerator for HL7 uses the following terms and definitions.</span></span>

## <a name="a"></a><span data-ttu-id="b1084-105">只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，</span><span class="sxs-lookup"><span data-stu-id="b1084-105">A</span></span>    
 <span data-ttu-id="b1084-106">**成品**  </span><span class="sxs-lookup"><span data-stu-id="b1084-106">**artifact**  </span></span>  
 <span data-ttu-id="b1084-107">構成 HL7 V3.0 選票成品可探索、 分析和設計活動導致訊息規格建立所產生的交付項目。</span><span class="sxs-lookup"><span data-stu-id="b1084-107">The artifacts that comprise the HL7 V3.0 ballot are the deliverables resulting from the discovery, analysis, and design activities leading to the creation of message specifications.</span></span>  
  
 <span data-ttu-id="b1084-108">HL7 V3.0 標準內文件所組成的元件是成品。</span><span class="sxs-lookup"><span data-stu-id="b1084-108">Within the HL7 V3.0 standards, the components that make up the documentation are artifacts.</span></span> <span data-ttu-id="b1084-109">這包括分鏡腳本、 應用程式角色、 觸發程序事件、 領域訊息資訊模型規格 (D-MIMs)、 精簡的訊息資訊模型規格 (R MIMs)、 階層式的訊息描述 specificatins(HMDs)、 訊息類型和互動。</span><span class="sxs-lookup"><span data-stu-id="b1084-109">This includes storyboards, application roles, trigger events, Domain Message Information Model specifications (D-MIMs), Refined Message Information Model specifications (R-MIMs), Hierarchical Message Description specificatins(HMDs), message types, and interactions.</span></span>  
  
 <span data-ttu-id="b1084-110">**成品識別碼**  </span><span class="sxs-lookup"><span data-stu-id="b1084-110">**artifact identifier**  </span></span>  
 <span data-ttu-id="b1084-111">Technical Committee 送出，並提供每個成品由串連子區段、 網域和成品的程式碼、 6 位數、 無意義的數字，2 位數的領域程式碼和 2 位數的版本號碼指派的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="b1084-111">A Technical Committee submits and gives each artifact a unique identifier that is assigned by concatenating the subsection, domain and artifact code, a 6-digit, non-meaningful number, a 2-digit Realm code, and a 2-digit version number.</span></span>  

## <a name="c"></a><span data-ttu-id="b1084-112">c</span><span class="sxs-lookup"><span data-stu-id="b1084-112">C</span></span>
  
 <span data-ttu-id="b1084-113">**基數**  </span><span class="sxs-lookup"><span data-stu-id="b1084-113">**cardinality**  </span></span>  
 <span data-ttu-id="b1084-114">資料元素 （資料元素可能會重複次數內的物件檢視的個別發生次數） 或階層式的訊息描述 （最小和最大數目的項目之訊息項目） 中的資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="b1084-114">The property of a data element (the number of times a data element may repeat within an individual occurrence of an object view) or column in the Hierarchical Message Description (the minimum and maximum number of occurrences of the message element).</span></span> <span data-ttu-id="b1084-115">請參閱階層式的訊息描述。</span><span class="sxs-lookup"><span data-stu-id="b1084-115">See Hierarchical Message Description.</span></span>  
  
## <a name="d"></a><span data-ttu-id="b1084-116">D</span><span class="sxs-lookup"><span data-stu-id="b1084-116">D</span></span>   
 <span data-ttu-id="b1084-117">**網域**</span><span class="sxs-lookup"><span data-stu-id="b1084-117">**domain**</span></span>    
 1. <span data-ttu-id="b1084-118">問題的一組 HL7 訊息或 （「 應用程式網域 」） 的系統處理的主旨。</span><span class="sxs-lookup"><span data-stu-id="b1084-118">The problem or subject to be addressed by a set of HL7 messages or by a system ("application domain").</span></span> <span data-ttu-id="b1084-119">健康照護中感興趣的特定區域。</span><span class="sxs-lookup"><span data-stu-id="b1084-119">A particular area of interest in health care.</span></span> 
 2. <span data-ttu-id="b1084-120">可能的值的資料型別、 屬性或資料類型的元件組。</span><span class="sxs-lookup"><span data-stu-id="b1084-120">The set of possible values of a data type, attribute, or data type component.</span></span> <span data-ttu-id="b1084-121">請參閱詞彙網域。</span><span class="sxs-lookup"><span data-stu-id="b1084-121">See vocabulary domain.</span></span> 
 3. <span data-ttu-id="b1084-122">HL7，例如 Pharmacy 實驗室，病患管理內專題討論群組。</span><span class="sxs-lookup"><span data-stu-id="b1084-122">An interest group within HL7, such as Pharmacy, Laboratory, Patient Administration.</span></span>  
  
## <a name="e"></a><span data-ttu-id="b1084-123">E</span><span class="sxs-lookup"><span data-stu-id="b1084-123">E</span></span> 
 <span data-ttu-id="b1084-124">**事件**</span><span class="sxs-lookup"><span data-stu-id="b1084-124">**event**</span></span>    
 1. <span data-ttu-id="b1084-125">刺激造成值得注意的狀態變更的物件。</span><span class="sxs-lookup"><span data-stu-id="b1084-125">A stimulus that causes a noteworthy state change of an object.</span></span> <span data-ttu-id="b1084-126">叫用物件的行為訊號。</span><span class="sxs-lookup"><span data-stu-id="b1084-126">A signal that invokes the behavior of an object.</span></span> <span data-ttu-id="b1084-127">請參閱觸發程序事件。</span><span class="sxs-lookup"><span data-stu-id="b1084-127">See trigger event.</span></span> 
 2. <span data-ttu-id="b1084-128">情緒詞彙網域值。</span><span class="sxs-lookup"><span data-stu-id="b1084-128">A vocabulary domain value for Mood.</span></span>  
  
 
## <a name="h"></a><span data-ttu-id="b1084-129">H</span><span class="sxs-lookup"><span data-stu-id="b1084-129">H</span></span>
<span data-ttu-id="b1084-130">**階層式的訊息描述 (HMD)**  </span><span class="sxs-lookup"><span data-stu-id="b1084-130">**Hierarchical Message Description (HMD)**  </span></span>  
 <span data-ttu-id="b1084-131">訊息及其群組、 序列、 選擇性和基數的確切欄位規格。</span><span class="sxs-lookup"><span data-stu-id="b1084-131">A specification of the exact fields of a message and their grouping, sequence, optionality, and cardinality.</span></span> <span data-ttu-id="b1084-132">含有一或多個互動的訊息類型，或代表一或多個常見的訊息項目類型。</span><span class="sxs-lookup"><span data-stu-id="b1084-132">Either contains message types for one or more interactions or represents one or more common message element types.</span></span> <span data-ttu-id="b1084-133">這是主要標準 HL7 訊息結構。</span><span class="sxs-lookup"><span data-stu-id="b1084-133">This is the primary normative structure for HL7 messages.</span></span>  
  
## <a name="m"></a><span data-ttu-id="b1084-134">M</span><span class="sxs-lookup"><span data-stu-id="b1084-134">M</span></span>  
 <span data-ttu-id="b1084-135">**必要項目**  </span><span class="sxs-lookup"><span data-stu-id="b1084-135">**mandatory**  </span></span>  
 <span data-ttu-id="b1084-136">階層式訊息描述 (HMD) 資料行。</span><span class="sxs-lookup"><span data-stu-id="b1084-136">A column in the Hierarchical Message Description (HMD).</span></span> <span data-ttu-id="b1084-137">如果屬性強制性，此屬性為基礎的所有訊息項目包含必須包含非 null 值，或必須有預設值不是 null。</span><span class="sxs-lookup"><span data-stu-id="b1084-137">If the inclusion for an attribute mandatory, all message elements based on this attribute must contain a non-null value, or they must have a default that is not null.</span></span>  
  
  
 <span data-ttu-id="b1084-138">**訊息**  </span><span class="sxs-lookup"><span data-stu-id="b1084-138">**message**  </span></span>  
 <span data-ttu-id="b1084-139">從應用程式的不同而不同，傳達的資訊套件。</span><span class="sxs-lookup"><span data-stu-id="b1084-139">A package of information communicated from one application to another.</span></span> <span data-ttu-id="b1084-140">請參閱訊息類型和訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1084-140">See message type and message instance.</span></span>  
  
 <span data-ttu-id="b1084-141">**訊息的開發架構 (MDF)**  </span><span class="sxs-lookup"><span data-stu-id="b1084-141">**Message Development Framework (MDF)**  </span></span>  
 <span data-ttu-id="b1084-142">模型、 方法和工具構成指定 HL7 V3.0 訊息的方法集合。</span><span class="sxs-lookup"><span data-stu-id="b1084-142">The collection of models, methods, and tools that comprise the methodology for specifying HL7 V3.0 messages.</span></span> <span data-ttu-id="b1084-143">HL7 標準的開發人員使用此架構。</span><span class="sxs-lookup"><span data-stu-id="b1084-143">Developers of the HL7 standards use this framework.</span></span> <span data-ttu-id="b1084-144">V3.0 指南摘要說明內容的方法。</span><span class="sxs-lookup"><span data-stu-id="b1084-144">The V3.0 Guide summarizes the content of the methodology.</span></span>  
  
 <span data-ttu-id="b1084-145">**訊息項目**  </span><span class="sxs-lookup"><span data-stu-id="b1084-145">**message element**  </span></span>  
 <span data-ttu-id="b1084-146">結構內的訊息類型的單位。</span><span class="sxs-lookup"><span data-stu-id="b1084-146">A unit of structure within a message type.</span></span>  
  
 <span data-ttu-id="b1084-147">**訊息項目類型**  </span><span class="sxs-lookup"><span data-stu-id="b1084-147">**message element type**  </span></span>  
 <span data-ttu-id="b1084-148">訊息類型，描述其中一個項目訊息的部分。</span><span class="sxs-lookup"><span data-stu-id="b1084-148">A portion of a message type that describes one of the elements of the message.</span></span>  
  
 <span data-ttu-id="b1084-149">**訊息執行個體**  </span><span class="sxs-lookup"><span data-stu-id="b1084-149">**message instance**  </span></span>  
 <span data-ttu-id="b1084-150">格式化為特定的傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="b1084-150">A message that is formatted for a specific transmission.</span></span> <span data-ttu-id="b1084-151">相同的訊息類型可以描述兩個訊息和識別具有相同的互動和尚未改變執行個體中因為變化值、 目前狀態，或不存在，正在傳送的資料和不同基數的集合。</span><span class="sxs-lookup"><span data-stu-id="b1084-151">The same message type can describe two messages  and identify with the same interaction and yet vary in the instance because of variations in values, presence, or absence of the data being sent and different cardinalities of collections.</span></span> <span data-ttu-id="b1084-152">否則相同的訊息可能會不同執行個體，如果在不同時間或依不同的寄件者傳送。</span><span class="sxs-lookup"><span data-stu-id="b1084-152">Otherwise, identical messages may be different instances if they are sent at different times or by a different sender.</span></span>  
  
 <span data-ttu-id="b1084-153">**訊息內容**  </span><span class="sxs-lookup"><span data-stu-id="b1084-153">**message payload**  </span></span>  
 <span data-ttu-id="b1084-154">資料執行中的訊息。</span><span class="sxs-lookup"><span data-stu-id="b1084-154">Data carried in a message.</span></span>  
  
 <span data-ttu-id="b1084-155">**訊息類型**  </span><span class="sxs-lookup"><span data-stu-id="b1084-155">**message type**  </span></span>  
 <span data-ttu-id="b1084-156">指定在階層式訊息描述 (HMD) 的訊息項目組織。</span><span class="sxs-lookup"><span data-stu-id="b1084-156">The organization of message elements that is specified in a Hierarchical Message Description (HMD).</span></span> <span data-ttu-id="b1084-157">每個訊息類型會與溝通互動模型中的一或多個互動的一部分。</span><span class="sxs-lookup"><span data-stu-id="b1084-157">Each message type is communicated as part of one or more interactions in the interaction model.</span></span> <span data-ttu-id="b1084-158">訊息類型實際上會構成一組建構訊息，提供一組特定的執行個體資料的規則。</span><span class="sxs-lookup"><span data-stu-id="b1084-158">A message type in effect constitutes a set of rules for constructing a message given a specific set of instance data.</span></span> <span data-ttu-id="b1084-159">它也會定義用於剖析訊息，以復原的執行個體資料的規則。</span><span class="sxs-lookup"><span data-stu-id="b1084-159">It also defines the rules for parsing a message to recover the instance data.</span></span> <span data-ttu-id="b1084-160">訊息類型無關實作的技術規格，因此，如果相同的資料會使用相同的訊息類型和不同的實作技術規格，可以從兩個不同中音譯訊息類型。</span><span class="sxs-lookup"><span data-stu-id="b1084-160">The message type is independent of the Implementation Technology Specification, so that if the same data is sent using the same message type and different implementation technology specifications, the message type can be transliterated from one to the other.</span></span>  

## <a name="p"></a><span data-ttu-id="b1084-161">P</span><span class="sxs-lookup"><span data-stu-id="b1084-161">P</span></span>  
 <span data-ttu-id="b1084-162">**屬性**  </span><span class="sxs-lookup"><span data-stu-id="b1084-162">**property**  </span></span>  
 <span data-ttu-id="b1084-163">任何屬性、 關聯、 方法或類別或物件定義的狀態模型。</span><span class="sxs-lookup"><span data-stu-id="b1084-163">Any attribute, association, method, or state model defined for a class or object.</span></span> <span data-ttu-id="b1084-164">在 HMD，資料行表示的類別、 屬性或關聯角色名稱，因為它會顯示參考資訊模型 (RIM) 中。</span><span class="sxs-lookup"><span data-stu-id="b1084-164">In an HMD, the column that states the name of the class, attribute, or association role name as it appears in the Reference Information Model (RIM).</span></span>  

## <a name="r"></a><span data-ttu-id="b1084-165">R</span><span class="sxs-lookup"><span data-stu-id="b1084-165">R</span></span>  
 <span data-ttu-id="b1084-166">**參考資訊模型 (RIM)**  </span><span class="sxs-lookup"><span data-stu-id="b1084-166">**Reference Information Model (RIM)**  </span></span>  
 <span data-ttu-id="b1084-167">從其他所有資訊模型 (例如 MIMs R) 和訊息衍生 HL7 資訊模型。</span><span class="sxs-lookup"><span data-stu-id="b1084-167">The HL7 information model from which all other information models (for example, R-MIMs) and messages derive.</span></span>  
  
 <span data-ttu-id="b1084-168">**調整過的訊息資訊模型 (R MIM)**  </span><span class="sxs-lookup"><span data-stu-id="b1084-168">**Refined Message Information Model (R-MIM)**  </span></span>  
 <span data-ttu-id="b1084-169">表示一組訊息的需求資訊結構。</span><span class="sxs-lookup"><span data-stu-id="b1084-169">An information structure that represents the requirements for a set of messages.</span></span> <span data-ttu-id="b1084-170">可能包含從 RIM 類別，會複製的其他類別的邊緣條件約束的子集。</span><span class="sxs-lookup"><span data-stu-id="b1084-170">A constrained subset of the RIM that may contain additional classes that are cloned from RIM classes.</span></span> <span data-ttu-id="b1084-171">包含支援一或多個階層式訊息描述 (HMDs) 所需的類別、 屬性、 關聯和資料型別。</span><span class="sxs-lookup"><span data-stu-id="b1084-171">Contains those classes, attributes, associations, and data types that are needed to support one or more Hierarchical Message Description (HMDs).</span></span> <span data-ttu-id="b1084-172">單一訊息，可顯示為透過 R MIM 內類別的特定路徑。</span><span class="sxs-lookup"><span data-stu-id="b1084-172">A single message can be shown as a particular pathway through the classes within an R-MIM.</span></span>  

## <a name="s"></a><span data-ttu-id="b1084-173">S</span><span class="sxs-lookup"><span data-stu-id="b1084-173">S</span></span>  
 <span data-ttu-id="b1084-174">**案例**  </span><span class="sxs-lookup"><span data-stu-id="b1084-174">**scenario**  </span></span>  
 <span data-ttu-id="b1084-175">在統一的模型化語言 (UML)，「 執行透過單一使用案例的單一路徑 」。</span><span class="sxs-lookup"><span data-stu-id="b1084-175">In Unified Modeling Language (UML), "a single path of execution through a single use case".</span></span> <span data-ttu-id="b1084-176">陳述式的定義為一連串的互動中醫療保健相關的事件。</span><span class="sxs-lookup"><span data-stu-id="b1084-176">A statement of events defined as a sequence of interactions relevant in health care.</span></span> <span data-ttu-id="b1084-177">案例提供一組模型 committee 預期通常發生在網域中的互動。</span><span class="sxs-lookup"><span data-stu-id="b1084-177">The scenario provides one set of interactions that the modeling committee expects to typically occur in the domain.</span></span> <span data-ttu-id="b1084-178">通常，循序圖來顯示單一案例的互動的一組建構。</span><span class="sxs-lookup"><span data-stu-id="b1084-178">Usually, a sequence diagram is constructed to show a group of interactions for a single scenario.</span></span> <span data-ttu-id="b1084-179">每個案例中會顯示為互動模型的子集。</span><span class="sxs-lookup"><span data-stu-id="b1084-179">Each scenario is displayed as a subset of the interaction model.</span></span>  
  
 <span data-ttu-id="b1084-180">**schema**</span><span class="sxs-lookup"><span data-stu-id="b1084-180">**schema**</span></span>    
 1. <span data-ttu-id="b1084-181">圖表的簡報、 結構化的架構或計劃。</span><span class="sxs-lookup"><span data-stu-id="b1084-181">A diagrammatic presentation, a structured framework, or a plan.</span></span> 
 2. <span data-ttu-id="b1084-182">一組需求，必須符合才能讓文件或資料集是內容中的該語法有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="b1084-182">A set of requirements that need to be met in order for a document or set of data to be a valid expression within the context of that grammar.</span></span> <span data-ttu-id="b1084-183">XML 結構描述是規格中標準通用標記語言 (SGML) 的文件的結構或資料集。</span><span class="sxs-lookup"><span data-stu-id="b1084-183">An XML schema is a specification in Standard Generalized Markup Language (SGML) of the structure of a document or set of data.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b1084-184">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="b1084-184">Next steps</span></span>
[<span data-ttu-id="b1084-185">合作對象 - BTAHL7 設定總管</span><span class="sxs-lookup"><span data-stu-id="b1084-185">Parties - BTAHL7 Configuration Explorer</span></span>](parties-tab.md)  
[<span data-ttu-id="b1084-186">全域設定 - BTAHL7 設定總管</span><span class="sxs-lookup"><span data-stu-id="b1084-186">Global Settings - BTAHL7 Configuration Explorer</span></span>](global-settings-tab.md)  
[<span data-ttu-id="b1084-187">MLLP 傳輸屬性對話方塊 UI 說明</span><span class="sxs-lookup"><span data-stu-id="b1084-187">MLLP Transport Properties Dialog Box UI Help</span></span>](mllp-transport-properties-dialog-box-ui-help.md)