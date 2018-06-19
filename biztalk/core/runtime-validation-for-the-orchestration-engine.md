---
title: 協調流程引擎的執行階段驗證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- validating, assemblies
- orchestrations, validating
- validating, orchestration engine
- schemas, validating
- correlations, validating
- validating, schemas
- orchestration engine, runtime validation
- assemblies, validating
- validating, correlations
- validating, orchestrations
- validating
ms.assetid: f6085889-05d6-4eba-a528-9d034c4e4225
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e53adb5aa42c7dfe23df50707754bde200ea838a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269262"
---
# <a name="runtime-validation-for-the-orchestration-engine"></a><span data-ttu-id="33499-102">協調流程引擎的執行階段驗證</span><span class="sxs-lookup"><span data-stu-id="33499-102">Runtime Validation for the Orchestration Engine</span></span>
<span data-ttu-id="33499-103">您可以設定協調流程引擎以執行各種執行階段驗證，以協助您測試協調流程和診斷可能發生的組態或資料錯誤。</span><span class="sxs-lookup"><span data-stu-id="33499-103">You can configure the orchestration engine to perform various runtime validations that can help you test your orchestration and diagnose configuration or data errors that might arise.</span></span>  
  
 <span data-ttu-id="33499-104">您可以在 BTSNTSvc.exe.config 中設定旗標，而您可以在與 BTSNTSvc.exe 相同的目錄中建立或編輯 BTSNTSvc.exe.config 組態檔 (通常是在 BizTalk 部署目錄中)。</span><span class="sxs-lookup"><span data-stu-id="33499-104">You can set flags in BTSNTSvc.exe.config, a configuration file that you can create or edit in the same directory as BTSNTSvc.exe (normally in the BizTalk deployment directory).</span></span> <span data-ttu-id="33499-105">您可在 BTSNTSvc.exe.config 檔案中設定下列旗標：</span><span class="sxs-lookup"><span data-stu-id="33499-105">You can set the following flags in the BTSNTSvc.exe.config file:</span></span>  
  
-   <span data-ttu-id="33499-106">如果您設定**ValidateAssemblies**旗標設為`True`，引擎嘗試載入立即依存組件的協調流程，並在失敗會擲回後所參考的所有組件Microsoft.XLANGs.Core.AssemblyValidationException。</span><span class="sxs-lookup"><span data-stu-id="33499-106">If you set the **ValidateAssemblies** flag to `True`, the engine tries to load all assemblies referenced by immediate dependent assemblies of an orchestration and upon failure throws Microsoft.XLANGs.Core.AssemblyValidationException.</span></span>  
  
-   <span data-ttu-id="33499-107">如果您設定**ValidateSchemas**旗標設為`True`，此引擎會使用 System.Xml.XmlValidatingReader 來驗證代表訊息部分類型的每個結構描述，並在失敗時擲回 System.Xml.XmlException。</span><span class="sxs-lookup"><span data-stu-id="33499-107">If you set the **ValidateSchemas** flag to `True`, the engine uses System.Xml.XmlValidatingReader to validate every schema representing a message part type and upon failure throws System.Xml.XmlException.</span></span>  
  
-   <span data-ttu-id="33499-108">如果您設定**ValidateCorrelations**旗標設為`True`，引擎就會確認，在平行群組的符合其中一個群組會收到具有相同的相互關聯屬性值，並在失敗時擲回的所有訊息Microsoft.XLANGs.Core.CorrelationValidationException。</span><span class="sxs-lookup"><span data-stu-id="33499-108">If you set the **ValidateCorrelations** flag to `True`, the engine verifies that in a parallel convoy all messages that match one of the convoy receives have the same correlation property values and upon failure throws Microsoft.XLANGs.Core.CorrelationValidationException.</span></span>  
  
-   <span data-ttu-id="33499-109">如果您設定**ExtendedLogging**旗標設為`True`，引擎在 Microsoft.XLANGs.BaseTypes.PublishMessageException 的資訊無法發行之訊息中顯示的升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="33499-109">If you set the **ExtendedLogging** flag to `True`, the engine displays the promoted properties in the information for Microsoft.XLANGs.BaseTypes.PublishMessageException for the message that failed to publish.</span></span>  
  
 <span data-ttu-id="33499-110">若要停用驗證，可以從組態檔整個移除旗標。</span><span class="sxs-lookup"><span data-stu-id="33499-110">If you want to disable a validation, remove the flag entirely from the configuration file.</span></span> <span data-ttu-id="33499-111">當所有驗證都開啟時，引擎將會驗證組件、結構描述和相互關聯。</span><span class="sxs-lookup"><span data-stu-id="33499-111">When all validations are on, the engine will validate assemblies, schemas, and correlation.</span></span> <span data-ttu-id="33499-112">如需詳細資訊和 BTSNTSvc.exe.config 的範例，請參閱[協調流程引擎組態](../core/orchestration-engine-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="33499-112">For more information and examples of BTSNTSvc.exe.config, see [Orchestration Engine Configuration](../core/orchestration-engine-configuration.md).</span></span>  
  
## <a name="validate-assemblies"></a><span data-ttu-id="33499-113">驗證組件</span><span class="sxs-lookup"><span data-stu-id="33499-113">Validate Assemblies</span></span>  
 <span data-ttu-id="33499-114">協調流程引擎將會驗證協調流程參考的所有組件是否為可用。</span><span class="sxs-lookup"><span data-stu-id="33499-114">The orchestration engine will verify that any assemblies referenced by the orchestration are available.</span></span> <span data-ttu-id="33499-115">若要讓驗證成功，在協調流程的第一個執行個體啟動時，所有參考的組件都必須在「全域組件快取」(GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="33499-115">For the validation to succeed, all referenced assemblies must be in the Global Assembly Cache (GAC) when the first instance of the orchestration is activated.</span></span> <span data-ttu-id="33499-116">若驗證失敗，會在應用程式記錄檔中記錄錯誤並擱置協調流程。</span><span class="sxs-lookup"><span data-stu-id="33499-116">If the validation fails, an error will be logged to the application log and the orchestration will be suspended.</span></span>  
  
## <a name="validate-schemas"></a><span data-ttu-id="33499-117">驗證結構描述</span><span class="sxs-lookup"><span data-stu-id="33499-117">Validate Schemas</span></span>  
 <span data-ttu-id="33499-118">不論何時指派 XSD 部分，協調流程引擎都會依照其結構描述驗證該部分的資料。</span><span class="sxs-lookup"><span data-stu-id="33499-118">Any time an XSD part is assigned, the orchestration engine will validate the part's data against its schema.</span></span> <span data-ttu-id="33499-119">如果驗證失敗，錯誤會記錄應用程式記錄檔，並將擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="33499-119">If the validation fails, the error will be logged to the application log and an exception will be thrown.</span></span>  
  
## <a name="validate-correlation"></a><span data-ttu-id="33499-120">驗證相互關聯</span><span class="sxs-lookup"><span data-stu-id="33499-120">Validate Correlation</span></span>  
 <span data-ttu-id="33499-121">協調流程引擎將會確認使用協調流程的指定執行個體為相互關聯指定的屬性值，是否反映在從協調流程執行個體傳送的任何訊息中。</span><span class="sxs-lookup"><span data-stu-id="33499-121">The orchestration engine will confirm that the property values that are specified for correlation with a given instance of an orchestration are reflected in any messages that are sent from that orchestration instance.</span></span> <span data-ttu-id="33499-122">如果**validateCorrelation**未設定，引擎會假設傳送的訊息會包含正確的相互關聯值，並且將會執行任何檢查。</span><span class="sxs-lookup"><span data-stu-id="33499-122">If **validateCorrelation** is not set, the engine will assume that the sent message contains the correct correlation values, and no check will be performed.</span></span>  
  
 <span data-ttu-id="33499-123">如果任何相互關聯驗證失敗，引擎會應用程式記錄檔中記錄錯誤並擲回例外狀況型別的**CorrelationValidationException**。</span><span class="sxs-lookup"><span data-stu-id="33499-123">If any correlation validation fails, the engine will log an error to the application log and throw an exception of type **CorrelationValidationException**.</span></span>  
  
 <span data-ttu-id="33499-124">根據預設， **validateCorrelation**未設定。</span><span class="sxs-lookup"><span data-stu-id="33499-124">By default, **validateCorrelation** is not set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33499-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33499-125">See Also</span></span>  
 <span data-ttu-id="33499-126">[偵錯協調流程](../core/debugging-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="33499-126">[Debugging Orchestrations](../core/debugging-orchestrations.md) </span></span>  
 [<span data-ttu-id="33499-127">協調流程引擎組態</span><span class="sxs-lookup"><span data-stu-id="33499-127">Orchestration Engine Configuration</span></span>](../core/orchestration-engine-configuration.md)