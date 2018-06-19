---
title: 如何將 64 位元成品新增至應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- artifacts, 64-bit support
- scripts, 64-bit support
- virtual directories, 64-bit support
- artifacts, applications
- 64-bit support, COM components
- 64-bit support, virtual directories
- applications, artifacts
- 64-bit support, scripts
- 64-bit support, artifacts
- COM components, 64-bit support
- BizTalk Server, 64-bit support
- applications, 64-bit support
ms.assetid: 46aca7d4-c5be-421e-b16d-7f3095c8cc67
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69707401fee8b7f48b30a79bab166a9f22c29a89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246622"
---
# <a name="how-to-add-a-64-bit-artifact-to-an-application"></a>如何將 64 位元成品新增至應用程式
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含 64 位元應用程式的支援。 這表示您可以用與 32 位元成品相同的方式，將 64 位元成品新增到 BizTalk 應用程式，然而，在 32 位元電腦上安裝下列 64 位元成品時，您可能會遇到下列問題：  
  
-   **從 Web 伺服器正在執行的 64 位元工作者處理序的虛擬目錄。** 這個虛擬目錄會安裝到 32 位元電腦上，不過可能不會正確運作。 會記錄一項不相符狀況。  
  
-   **Unmanaged 的 COM 或 Managed COM + 元件會標示為 64 位元。** 這些元件不會安裝到 32 位元電腦。  
  
-   **64 位元指令碼儲存為.exe 檔案。** 這種類型的指令碼可能不會正確運作。  
  
 如需新增成品的一般指示，請參閱[如何建立或新增成品](../core/how-to-create-or-add-an-artifact.md)。 如需新增特定成品類型的指示，請參閱[管理成品](../core/managing-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)   
 [如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)