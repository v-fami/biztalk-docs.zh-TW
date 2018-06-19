---
title: 如何建立和修改配接器群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1eef051-2ed7-4e28-8cb9-0145d6c8ed76
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6865de8eb67d9fe1a6ca8d93b7d2e6527ae36364
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249222"
---
# <a name="how-to-create-and-modify-an-adapter-group"></a>如何建立和修改配接器群組
單一登入 (SSO) 的其中一項新功能是能夠建立和修改配接器群組。 配接器群組正如其名，就是配接器的組合。 您可以使用配接器群組來組織配接器的安全性設定及其他屬性。  
  
### <a name="to-create-and-modify-an-adapter-group"></a>若要建立和修改配接器群組  
  
1.  使用 SSOPS 工具的呼叫來建立配接器群組。  
  
     在關聯的 XML 檔案中，必須將群組旗標設定為配接器群組。  
  
2.  使用 `ISSOPSAdmin.AddAdapterToAdapterGroup` 新增一或多個配接器到配接器群組。  
  
     此時，配接器群組已準備就緒可供使用。 如有必要，可使用 `ISSOPSAdmin.GetAdaptersForAdapterGroup` 檢視關聯配接器的完整清單。  
  
3.  您可以使用 `ISSOPSAdmin.SetAdapterProperties` 修改配接器群組的設定。  
  
4.  完成後，就可以使用 `ISSOPSAdmin.RemoveAdapterFromAdapterGroup` 從配接器群組中移除配接器。  
  
5.  最後，您可以使用 `ISSOAdmin.DeleteApplication` 刪除配接器群組。  
  
     或者，可以改用 SSOPS 工具的 `-delete` 命令刪除配接器群組。  
  
## <a name="see-also"></a>另請參閱  
 [同步處理密碼](../core/synchronizing-passwords.md)