---
title: MQSeries 配接器的命令列組態精靈 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [MQSeries adapters], silent configuration
- MQSeries adapters, silent configuration
- configuring [MQSeries adapters], Command-Line Configuration Wizard
- Command-Line Configuration Wizard
- MQSeries adapters, Command-Line Configuration Wizard
ms.assetid: cab905d1-fe19-4d6a-be1b-f561e133e1d2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee73b890fca43a3651f22092486e5898862b0b72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232054"
---
# <a name="command-line-configuration-wizard-for-the-mqseries-adapter"></a><span data-ttu-id="a0e79-102">MQSeries 配接器的命令列組態精靈</span><span class="sxs-lookup"><span data-stu-id="a0e79-102">Command-Line Configuration Wizard for the MQSeries Adapter</span></span>
<span data-ttu-id="a0e79-103">此精靈在安裝、解除安裝和記錄動作方面有四個選項。</span><span class="sxs-lookup"><span data-stu-id="a0e79-103">The wizard has four options for installing, uninstalling, and logging actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e79-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0e79-104">Syntax</span></span>  
 <span data-ttu-id="a0e79-105">**mqsconfigwiz [/u] [/i config.xml] [/l 記錄檔] [/？]**</span><span class="sxs-lookup"><span data-stu-id="a0e79-105">**mqsconfigwiz [/u] [/i config.xml] [/l logfile] [/?]**</span></span>  
  
|<span data-ttu-id="a0e79-106">選項</span><span class="sxs-lookup"><span data-stu-id="a0e79-106">Option</span></span>|<span data-ttu-id="a0e79-107">Description</span><span class="sxs-lookup"><span data-stu-id="a0e79-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a0e79-108">**/u**</span><span class="sxs-lookup"><span data-stu-id="a0e79-108">**/u**</span></span>|<span data-ttu-id="a0e79-109">解除安裝 MQSAgent。</span><span class="sxs-lookup"><span data-stu-id="a0e79-109">Uninstalls the MQSAgent.</span></span>|  
|<span data-ttu-id="a0e79-110">**/i** *config.xml*</span><span class="sxs-lookup"><span data-stu-id="a0e79-110">**/i** *config.xml*</span></span>|<span data-ttu-id="a0e79-111">安裝 MQSAgent 使用檔案中的資訊*config.xml*。</span><span class="sxs-lookup"><span data-stu-id="a0e79-111">Installs the MQSAgent using the information in the file *config.xml*.</span></span>|  
|<span data-ttu-id="a0e79-112">**/l** *記錄檔*</span><span class="sxs-lookup"><span data-stu-id="a0e79-112">**/l** *logfile*</span></span>|<span data-ttu-id="a0e79-113">動作記錄檔案*logfile*。</span><span class="sxs-lookup"><span data-stu-id="a0e79-113">Logs actions to the file *logfile*.</span></span>|  
|<span data-ttu-id="a0e79-114">**/?**</span><span class="sxs-lookup"><span data-stu-id="a0e79-114">**/?**</span></span>|<span data-ttu-id="a0e79-115">顯示描述命令列選項的對話方塊</span><span class="sxs-lookup"><span data-stu-id="a0e79-115">Displays a dialog box describing the command-line options.</span></span>|  
  
 <span data-ttu-id="a0e79-116">包含組態資訊的 XML 檔案內容會依據您所使用的 Windows 版本而有所不同。</span><span class="sxs-lookup"><span data-stu-id="a0e79-116">The contents of the XML file that contains the configuration information may vary, depending on the version of Windows you are using.</span></span> <span data-ttu-id="a0e79-117">如需組態檔格式的詳細資訊，請參閱[MQSeries 配接器的 XML 組態檔](../core/xml-configuration-file-for-the-mqseries-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e79-117">For more information about the configuration file format, see [XML Configuration File for the MQSeries Adapter](../core/xml-configuration-file-for-the-mqseries-adapter.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0e79-118">執行組態精靈時，配接器無法運作。</span><span class="sxs-lookup"><span data-stu-id="a0e79-118">The adapter does not work while the configuration wizard is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0e79-119">您無法使用命令列組態精靈來重新設定 MQSAgent。</span><span class="sxs-lookup"><span data-stu-id="a0e79-119">You cannot reconfigure MQSAgent with the command-line configuration wizard.</span></span> <span data-ttu-id="a0e79-120">您必須先執行精靈解除安裝代理程式 (**/u**)，然後執行它來進行設定 (**/i**)。</span><span class="sxs-lookup"><span data-stu-id="a0e79-120">You must first run the wizard to uninstall the agent (**/u**), and then run it to configure (**/i**).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e79-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0e79-121">See Also</span></span>  
 [<span data-ttu-id="a0e79-122">MQSeries 配接器的無訊息組態</span><span class="sxs-lookup"><span data-stu-id="a0e79-122">Silent Configuration of the MQSeries Adapter</span></span>](../core/silent-configuration-of-the-mqseries-adapter.md)