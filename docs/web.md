#web  
1.网站的Web端，基于Flask搭建，采用 MTV 的设计思想。  
2.以下为整个工程下Web端的目录列表。区块引用（即名称左侧有一竖线处）表示该路径的最深处。  

* ##youmu  
    * ###api：本系统基于Flask框架构建，此目录是其API
		* ####barrage：弹幕相关模块
			\_\_init\_\_.py  
			\_\_init\_\_.pyc  
			service.py  
			service.pyc  
			views.py  
			views.pyc  

		* ####comment: 评论相关模块
			\_\_init\_\_.py  
			\_\_init\_\_.pyc  
			service.py  
			service.pyc  
			views.py  
			views.pyc  

		* ####user：用户信息相关模块
			\_\_init\_\_.py  
			\_\_init\_\_.pyc  
			forms.py  
			forms.pyc  
			service.py  
			service.pyc  
			views.py  
			views.pyc  

		* ####video：视频信息相关模块
			\_\_init\_\_.py  
			\_\_init\_\_.pyc  
			service.py  
			service.pyc  
			views.py  
			views.pyc  

		* ####videolist：视频列表相关模块
			\_\_init\_\_.py  
			\_\_init\_\_.pyc  
			service.py  
			service.pyc  
			views.py  
			views.pyc  

		* \_\_init\_\_.py  
		* \_\_init\_\_.pyc  

	* ###clients：Mongo的客户端相关模块
		\_\_init\_\_.py  
		\_\_init\_\_.pyc  
		mongoclient.py  
		mongoclient.pyc  
		tunetclient.py  
		tunetclient.pyc  

	* ###frontend：框架的装饰器及模块的渲染
		\_\_init\_\_.py  
		\_\_init\_\_.pyc  
		views.py  
		views.pyc  

	* ###models：数据模型，包括弹幕、评论、用户管理、视频管理等
		\_\_init\_\_.py  
		\_\_init\_\_.pyc  
		barrage.py  
		barrage.pyc  
		comment.py  
		comment.pyc  
		user.py  
		user.pyc  
		video.py  
		video.pyc  

	* ###static：网页静态文件夹

		* ####css：CSS样式表
			base.css  
			docs.css  
			font-awesome.min.css  
			foundation.css  
			foundation.min.css  
			normalize.css  
			videojs_ABdm.css  
			video-js.css  

		* ####fonts：字体文件
			* #####svgs

				fi-address-book.svg  
				fi-alert.svg  
				fi-align-center.svg  
				fi-align-justify.svg  
				fi-align-left.svg  
				fi-align-right.svg  
				fi-anchor.svg  
				fi-annotate.svg  
				fi-archive.svg  
				fi-arrow-down.svg  
				fi-arrow-left.svg  
				fi-arrow-right.svg  
				fi-arrows-compress.svg  
				fi-arrows-expand.svg  
				fi-arrows-in.svg  
				fi-arrows-out.svg  
				fi-arrow-up.svg  
				fi-asl.svg  
				fi-asterisk.svg  
				fi-at-sign.svg  
				fi-background-color.svg  
				fi-battery-empty.svg  
				fi-battery-full.svg  
				fi-battery-half.svg  
				fi-bitcoin.svg  
				fi-bitcoin-circle.svg  
				fi-blind.svg  
				fi-bluetooth.svg  
				fi-bold.svg  
				fi-book.svg  
				fi-book-bookmark.svg  
				fi-bookmark.svg  
				fi-braille.svg  
				fi-burst.svg  
				fi-burst-new.svg  
				fi-burst-sale.svg  
				fi-calendar.svg  
				fi-camera.svg  
				fi-check.svg  
				fi-checkbox.svg  
				fi-clipboard.svg  
				fi-clipboard-notes.svg  
				fi-clipboard-pencil.svg  
				fi-clock.svg  
				fi-closed-caption.svg  
				fi-cloud.svg  
				fi-comment.svg  
				fi-comment-minus.svg  
				fi-comment-quotes.svg  
				fi-comments.svg  
				fi-comment-video.svg  
				fi-compass.svg  
				fi-contrast.svg  
				fi-credit-card.svg  
				fi-crop.svg  
				fi-crown.svg  
				fi-css3.svg  
				fi-database.svg  
				fi-die-five.svg  
				fi-die-four.svg  
				fi-die-one.svg  
				fi-die-six.svg  
				fi-die-three.svg  
				fi-die-two.svg  
				fi-dislike.svg  
				fi-dollar.svg  
				fi-dollar-bill.svg  
				fi-download.svg  
				fi-eject.svg  
				fi-elevator.svg  
				fi-euro.svg  
				fi-eye.svg  
				fi-fast-forward.svg  
				fi-female.svg  
				fi-female-symbol.svg  
				fi-filter.svg  
				fi-first-aid.svg  
				fi-flag.svg  
				fi-folder.svg  
				fi-folder-add.svg  
				fi-folder-lock.svg  
				fi-foot.svg  
				fi-foundation.svg  
				fi-graph-bar.svg  
				fi-graph-horizontal.svg  
				fi-graph-pie.svg  
				fi-graph-trend.svg  
				fi-guide-dog.svg  
				fi-hearing-aid.svg  
				fi-heart.svg  
				fi-home.svg  
				fi-html5.svg  
				fi-indent-less.svg  
				fi-indent-more.svg  
				fi-info.svg  
				fi-italic.svg  
				fi-key.svg  
				fi-laptop.svg  
				fi-layout.svg  
				fi-lightbulb.svg  
				fi-like.svg  
				fi-link.svg  
				fi-list.svg  
				fi-list-bullet.svg  
				fi-list-number.svg  
				fi-list-thumbnails.svg  
				fi-lock.svg  
				fi-loop.svg  
				fi-magnifying-glass.svg  
				fi-mail.svg  
				fi-male.svg  
				fi-male-female.svg  
				fi-male-symbol.svg  
				fi-map.svg  
				fi-marker.svg  
				fi-megaphone.svg  
				fi-microphone.svg  
				fi-minus.svg  
				fi-minus-circle.svg  
				fi-mobile.svg  
				fi-mobile-signal.svg  
				fi-monitor.svg  
				fi-mountains.svg  
				fi-music.svg  
				fi-next.svg  
				fi-no-dogs.svg  
				fi-no-smoking.svg  
				fi-page.svg  
				fi-page-add.svg  
				fi-page-copy.svg  
				fi-page-csv.svg  
				fi-page-delete.svg  
				fi-page-doc.svg  
				fi-page-edit.svg  
				fi-page-export.svg  
				fi-page-export-csv.svg  
				fi-page-export-doc.svg  
				fi-page-export-pdf.svg  
				fi-page-filled.svg  
				fi-page-multiple.svg  
				fi-page-pdf.svg  
				fi-page-remove.svg  
				fi-page-search.svg  
				fi-paint-bucket.svg  
				fi-paperclip.svg  
				fi-pause.svg  
				fi-paw.svg  
				fi-paypal.svg  
				fi-pencil.svg  
				fi-photo.svg  
				fi-play.svg  
				fi-play-circle.svg  
				fi-play-video.svg  
				fi-plus.svg  
				fi-pound.svg  
				fi-power.svg  
				fi-previous.svg  
				fi-price-tag.svg  
				fi-pricetag-multiple.svg  
				fi-print.svg  
				fi-prohibited.svg  
				fi-projection-screen.svg  
				fi-puzzle.svg  
				fi-quote.svg  
				fi-record.svg  
				fi-refresh.svg  
				fi-results.svg  
				fi-results-demographics.svg  
				fi-rewind.svg  
				fi-rewind-ten.svg  
				fi-rss.svg  
				fi-safety-cone.svg  
				fi-save.svg  
				fi-share.svg  
				fi-sheriff-badge.svg  
				fi-shield.svg  
				fi-shopping-bag.svg  
				fi-shopping-cart.svg  
				fi-shuffle.svg  
				fi-skull.svg  
				fi-social-500px.svg  
				fi-social-adobe.svg  
				fi-social-amazon.svg  
				fi-social-android.svg  
				fi-social-apple.svg  
				fi-social-behance.svg  
				fi-social-bing.svg  
				fi-social-blogger.svg  
				fi-social-delicious.svg  
				fi-social-designer-news.svg  
				fi-social-deviant-art.svg  
				fi-social-digg.svg  
				fi-social-dribbble.svg  
				fi-social-drive.svg  
				fi-social-dropbox.svg  
				fi-social-evernote.svg  
				fi-social-facebook.svg  
				fi-social-flickr.svg  
				fi-social-forrst.svg  
				fi-social-foursquare.svg  
				fi-social-game-center.svg  
				fi-social-github.svg  
				fi-social-google-plus.svg  
				fi-social-hacker-news.svg  
				fi-social-hi5.svg  
				fi-social-instagram.svg  
				fi-social-joomla.svg  
				fi-social-lastfm.svg  
				fi-social-linkedin.svg  
				fi-social-medium.svg  
				fi-social-myspace.svg  
				fi-social-orkut.svg  
				fi-social-path.svg  
				fi-social-picasa.svg  
				fi-social-pinterest.svg  
				fi-social-rdio.svg  
				fi-social-reddit.svg  
				fi-social-skillshare.svg  
				fi-social-skype.svg  
				fi-social-smashing-mag.svg  
				fi-social-snapchat.svg  
				fi-social-spotify.svg  
				fi-social-squidoo.svg  
				fi-social-stack-overflow.svg  
				fi-social-steam.svg  
				fi-social-stumbleupon.svg  
				fi-social-treehouse.svg  
				fi-social-tumblr.svg  
				fi-social-twitter.svg  
				fi-social-vimeo.svg  
				fi-social-windows.svg  
				fi-social-xbox.svg  
				fi-social-yahoo.svg  
				fi-social-yelp.svg  
				fi-social-youtube.svg  
				fi-social-zerply.svg  
				fi-social-zurb.svg  
				fi-sound.svg  
				fi-star.svg  
				fi-stop.svg  
				fi-strikethrough.svg  
				fi-subscript.svg  
				fi-superscript.svg  
				fi-tablet-landscape.svg  
				fi-tablet-portrait.svg  
				fi-target.svg  
				fi-target-two.svg  
				fi-telephone.svg  
				fi-telephone-accessible.svg  
				fi-text-color.svg  
				fi-thumbnails.svg  
				fi-ticket.svg  
				fi-torso.svg  
				fi-torso-business.svg  
				fi-torso-female.svg  
				fi-torsos.svg  
				fi-torsos-all.svg  
				fi-torsos-all-female.svg  
				fi-torsos-female-male.svg  
				fi-torsos-male-female.svg  
				fi-trash.svg  
				fi-trees.svg  
				fi-trophy.svg  
				fi-underline.svg  
				fi-universal-access.svg  
				fi-unlink.svg  
				fi-unlock.svg  
				fi-upload.svg  
				fi-upload-cloud.svg  
				fi-usb.svg  
				fi-video.svg  
				fi-volume.svg  
				fi-volume-none.svg  
				fi-volume-strike.svg  
				fi-web.svg  
				fi-wheelchair.svg  
				fi-widget.svg  
				fi-wrench.svg  
				fi-x.svg  
				fi-x-circle.svg  
				fi-yen.svg  
				fi-zoom-in.svg  
				fi-zoom-out.svg  
			* FontAwesome.otf  
			* fontawesome-webfont.eot  
			* fontawesome-webfont.svg  
			* fontawesome-webfont.ttf  
			* fontawesome-webfont.woff  
			* foundation-icons.css  
			* foundation-icons.eot  
			* foundation-icons.svg  
			* foundation-icons.ttf  
			* foundation-icons.woff  

		* ####img：图片文件
			human-head-with-question-mark.jpg  
			stone_lion_blurred.jpg  
			stone_lion.jpg  
			youmu.jpg  
			youmu-circle.png  
			youmu-seal.jpg  

		* ####js：js文件

			* #####CommentCoreLibrary  

				BilibiliFormat.js  
				CommentCoreLibrary.js  

			* #####foundation  

                foundation.abide.js  
				foundation.accordion.js  
				foundation.alert.js  
				foundation.clearing.js  
				foundation.dropdown.js  
				foundation.equalizer.js  
				foundation.interchange.js  
				foundation.joyride.js  
				foundation.js  
				foundation.magellan.js  
				foundation.offcanvas.js  
				foundation.orbit.js  
				foundation.reveal.js  
				foundation.slider.js  
				foundation.tab.js  
				foundation.tooltip.js  
				foundation.topbar.js  

			* #####vendor

				fastclick.js  
				jquery.cookie.js  
				jquery.form.js  
				jquery.js  
				jquery.stellar.min.js  
				modernizr.js  
				placeholder.js  

			* angular.min.js  
			* app.js  
			* foundation.min.js  
			* index.js  
			* main.js  
			* mm-foundation-tpls.min.js  
			* video.js  
			* videojs_ABdm.js  

		* ####sass：Sass样式表

			* #####breakpoints  

				_base.scss  
				_breakpoints.scss  
				_large.scss  
				_regular.scss  
				_small.scss  
				_smallest.scss  

			* #####modules  

				_modules.scss  

			* #####partials  

				_comments.scss  
				_footer.scss  
				_index.scss  
				_partials.scss  
				_top-bar.scss  
				_video.scss  

			* #####variables  

				_colors.scss  
				_fonts.scss  
				_variables.scss  

			* #####vendor  

				* #####bourbon  

					* #####addons  

						_button.scss  
						_clearfix.scss  
						_directional-values.scss  
						_ellipsis.scss  
						_font-family.scss  
						_hide-text.scss  
						_html5-input-types.scss  
						_position.scss  
						_prefixer.scss  
						_retina-image.scss  
						_size.scss  
						_timing-functions.scss  
						_triangle.scss  
						_word-wrap.scss  

					* #####css3  

						_animation.scss  
						_appearance.scss  
						_backface-visibility.scss  
						_background.scss  
						_background-image.scss  
						_border-image.scss  
						_border-radius.scss  
						_box-sizing.scss  
						_calc.scss  
						_columns.scss  
						_filter.scss  
						_flex-box.scss  
						_font-face.scss  
						_font-feature-settings.scss  
						_hidpi-media-query.scss  
						_hyphens.scss  
						_image-rendering.scss  
						_keyframes.scss  
						_linear-gradient.scss  
						_perspective.scss  
						_placeholder.scss  
						_radial-gradient.scss  
						_transform.scss  
						_transition.scss  
						_user-select.scss  

					* #####functions

						_assign.scss  
						_color-lightness.scss  
						_flex-grid.scss  
						_golden-ratio.scss  
						_grid-width.scss  
						_modular-scale.scss  
						_px-to-em.scss  
						_px-to-rem.scss  
						_strip-units.scss  
						_tint-shade.scss  
						_transition-property-name.scss  
						_unpack.scss  

					* #####helpers  

						_convert-units.scss  
						_gradient-positions-parser.scss  
						_is-num.scss  
						_linear-angle-parser.scss  
						_linear-gradient-parser.scss  
						_linear-positions-parser.scss  
						_linear-side-corner-parser.scss  
						_radial-arg-parser.scss  
						_radial-gradient-parser.scss  
						_radial-positions-parser.scss  
						_render-gradients.scss  
						_shape-size-stripper.scss  
						_str-to-num.scss  
					* #####settings  

						_asset-pipeline.scss  
						_prefixer.scss  
						_px-to-em.scss  

					* _bourbon.scss  
					* _bourbon-deprecated-upcoming.scss  

				* #####modular-scale  

					_calc.scss  
					_function.scss  
					_function-list.scss  
					_generate-list.scss  
					_pow.scss  
					_ratios.scss  
					_sort-list.scss  
					_tests.scss  

				* #####neat  

					* #####functions  

						_new-breakpoint.scss  
						_private.scss  

					* #####grid  

						_box-sizing.scss  
						_direction-context.scss  
						_display-context.scss  
						_fill-parent.scss  
						_media.scss  
						_omega.scss  
						_outer-container.scss  
						_pad.scss  
						_private.scss  
						_row.scss  
						_shift.scss  
						_span-columns.scss  
						_to-deprecate.scss  
						_visual-grid.scss  

					* #####settings  

						_disable-warnings.scss  
						_grid.scss  
						_visual-grid.scss

					* _neat.scss  
					* _neat-helpers.scss  
				* _modular-scale.scss  

			* _grid-settings.scss  
			* base.scss  

		* ####uploads：上传文件

			* #####images  

				uxa5m3R_save_5000_214503_1e-8.jpg  

			* #####videos  

				touch.txt  

		* #####video-js：video的js文件
			* #####font  

				vjs.eot  
				vjs.svg  
				vjs.ttf  
				vjs.woff  

			* #####lang  

				de.js  
				es.js  
				fr.js  
				it.js  
				ja.js  
				ko.js  
				nl.js  
				pt-BR.js  
				ru.js  
				uk.js  
				zh.js  

			* demo.captions.vtt  
			* demo.html  
			* video.dev.js  
			* video.js  
			* video-js.css  
			* video-js.less  
			* video-js.min.css  
			* video-js.swf  

		* comment.xml  

	* ###templates：网站界面模板目录

		* ####errors  

			forbidden_page.html  
			page_not_found.html  
			server_error.html  

		* ####partials  

			foot.html  
			head.html  
			topbar.html  

		* ####user  

			* #####partials  

				profile.html  
				tabs.html  
				users.html  
				videos.html  

			* index.html  

		* demo.html  
		* foundation-index.html  
		* index.html  
		* live.html  
		* player.html  
		* upload.html  
		* video.html  

	* \_\_init\_\_.py  
	* \_\_init\_\_.pyc  
	* app.py  
	* app.pyc  
	* config.py  
	* config.pyc  

* .gitignore  
* gulpfile.js  
* package.json  
* readme.md  
* requirements.txt  
* runserver.py  
* thuaccount.py  

* ##.git：Git用于跟踪管理版本库的Git仓库。

	* ###branches  

	* ###hooks  

		applypatch-msg.sample  
		commit-msg.sample  
		post-update.sample  
		pre-applypatch.sample  
		pre-commit.sample  
		prepare-commit-msg.sample  
		pre-push.sample  
		pre-rebase.sample  
		update.sample  

	* ###info  

		exclude

	* ###logs  

		* ####refs  

			* #####heads  

				master  

			* #####remotes  

				* #####origin  

					HEAD  

		HEAD 

	* ###objects  

		* ####info  

		* ####pack  

			pack-06f7fc4bb3c761731898e4d0494af250ee9ba0d7.idx  
			pack-06f7fc4bb3c761731898e4d0494af250ee9ba0d7.pack  

	* ###refs  
		* ####heads  
			master  
		* ####remotes  
			* #####origin  
				HEAD  

		* ####tags  
	* config  
	* description  
	* HEAD  
	* index  
	* packed-refs  

* ##logs  
