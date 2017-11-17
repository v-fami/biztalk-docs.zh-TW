---
title: "配接器組態的自訂下拉式編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a1b0961-652f-42b8-a18a-17abe9542cdd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b88e5eb887c2177783611ada8e3ce2a80a0b6a66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="custom-drop-down-editor-for-adapter-configuration"></a><span data-ttu-id="4bdf6-102">配接器組態的自訂下拉式編輯器</span><span class="sxs-lookup"><span data-stu-id="4bdf6-102">Custom Drop-Down Editor for Adapter Configuration</span></span>
<span data-ttu-id="4bdf6-103">自訂編輯器的程式碼會示範衍生自編輯器**System.Drawing.Design.UITypeEditor**類別，可顯示下拉式文字方塊中，供您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="4bdf6-103">The code for the custom editor shows an editor derived from the **System.Drawing.Design.UITypeEditor** class that displays a drop-down text box for entering a password.</span></span> <span data-ttu-id="4bdf6-104">**GetEditStyle**覆寫會傳回**UIEditorEditStyle.DropDown**表示下拉式子控制項。</span><span class="sxs-lookup"><span data-stu-id="4bdf6-104">The **GetEditStyle** override returns **UIEditorEditStyle.DropDown** to indicate a drop-down subcontrol.</span></span> <span data-ttu-id="4bdf6-105">服務方法**DropDownControl**和**CloseDropDown**管理與建立控制項**CreatePassword**。</span><span class="sxs-lookup"><span data-stu-id="4bdf6-105">The service methods **DropDownControl** and **CloseDropDown** manage the control created with **CreatePassword**.</span></span>  
  
 <span data-ttu-id="4bdf6-106">下列程式碼為此自訂下拉式編輯器的類別定義：</span><span class="sxs-lookup"><span data-stu-id="4bdf6-106">The following code is the class definition for the custom drop-down editor:</span></span>  
  
```  
/*************************************************************************  
 * Copyright (c) 1999-2004 Microsoft Corporation. All rights reserved.   *  
 *                                                                       *  
 * THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY *  
 * KIND, WHETHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE  *  
 * IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A PARTICULAR *  
 * PURPOSE. THE ENTIRE RISK OF USE OR RESULTS IN CONNECTION WITH THE USE *  
 * OF THIS CODE AND INFORMATION REMAINS WITH THE USER.                   *  
 *************************************************************************/  
  
using System;  
using System.ComponentModel;  
using System.Drawing.Design;  
using System.Windows.Forms;  
using System.Windows.Forms.Design;  
using System.Security;  
using System.Security.Permissions;  
using Microsoft.BizTalk.Adapter.Framework;  
using Microsoft.BizTalk.Adapter.Framework.Forms;  
  
namespace AdapterManagement.ComponentModel {  
   /// <summary>  
   /// PasswordUITypeEditor implements a user interface for acquiring passwords  
   /// within a visual designer.  
   /// </summary>  
   public class PasswordUITypeEditor : UITypeEditor {  
      public const char PasswordChar = '\u25cf';  
      private IWindowsFormsEditorService _service = null;  
      private TextBox _password = null;  
  
      [SecurityPermissionAttribute(SecurityAction.LinkDemand)]  
      public override UITypeEditorEditStyle GetEditStyle(ITypeDescriptorContext context) {  
         if (null != context && null != context.Instance) {  
            return UITypeEditorEditStyle.DropDown;  
         }  
         return base.GetEditStyle(context);  
      }  
  
      [SecurityPermissionAttribute(SecurityAction.LinkDemand)]  
      public override object EditValue(ITypeDescriptorContext context,   
                               IServiceProvider provider,  
                               object value) {  
         if (null != context && null != context.Instance && null != provider) {  
            this._service = (IWindowsFormsEditorService) provider.GetService   
                        (typeof(IWindowsFormsEditorService));  
            if (null != this._service) {  
               this._password = CreatePassword();  
               this._service.DropDownControl(this._password);  
               value = this._password.Text;  
            }  
         }  
         return value;  
      }  
  
      private TextBox CreatePassword () {  
         TextBox password = new TextBox();  
         password.PasswordChar = PasswordUITypeEditor.PasswordChar;  
         password.Leave += new EventHandler(password_Leave);  
      }  
  
      private void password_Leave(object sender, EventArgs e) {  
         if (null != this._service) {  
            this._service.CloseDropDown();  
         }  
      }  
   } // PasswordUITypeEditor  
} // Microsoft.BizTalk.Adapter.Framework.ComponentModel  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bdf6-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bdf6-107">See Also</span></span>  
 <span data-ttu-id="4bdf6-108">[自訂配接器組態設計工具](../core/custom-adapter-configuration-designer.md) </span><span class="sxs-lookup"><span data-stu-id="4bdf6-108">[Custom Adapter Configuration Designer](../core/custom-adapter-configuration-designer.md) </span></span>  
 <span data-ttu-id="4bdf6-109">[配接器組態的自訂強制回應對話方塊編輯器](../core/custom-modal-dialog-editor-for-adapter-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="4bdf6-109">[Custom Modal Dialog Editor for Adapter Configuration](../core/custom-modal-dialog-editor-for-adapter-configuration.md) </span></span>  
 <span data-ttu-id="4bdf6-110">[配接器組態的自訂類型轉換器](../core/custom-type-converter-for-adapter-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="4bdf6-110">[Custom Type Converter for Adapter Configuration](../core/custom-type-converter-for-adapter-configuration.md) </span></span>  
 [<span data-ttu-id="4bdf6-111">配接器的進階的組態元件</span><span class="sxs-lookup"><span data-stu-id="4bdf6-111">Advanced Configuration Components for Adapters</span></span>](../core/advanced-configuration-components-for-adapters.md)