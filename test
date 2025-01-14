! function() {
    "use strict";
    var t = {
            d: function(e, i) {
                for (var s in i) t.o(i, s) && !t.o(e, s) && Object.defineProperty(e, s, {
                    enumerable: !0,
                    get: i[s]
                })
            },
            o: function(t, e) {
                return Object.prototype.hasOwnProperty.call(t, e)
            },
            r: function(t) {
                "undefined" != typeof Symbol && Symbol.toStringTag && Object.defineProperty(t, Symbol.toStringTag, {
                    value: "Module"
                }), Object.defineProperty(t, "__esModule", {
                    value: !0
                })
            }
        },
        e = {};
    t.r(e), t.d(e, {
        Line: function() {
            return r
        },
        Physics: function() {
            return h
        },
        Point: function() {
            return c
        },
        Rect: function() {
            return d
        },
        Vector: function() {
            return o
        },
        getSignedDistance: function() {
            return l
        },
        toVector: function() {
            return s
        }
    });
    var i = JSON.parse('{"SYSTEM_LAYER":0,"ENTITIES_LAYER":1,"ESP_LAYER":2,"defaultViewport":{"width":1920,"height":1080,"zoom":0.9},"map":{"width":420,"height":515,"middleSize":[210,257.5]},"colors":{"map":"rgba(13, 13, 13, 1)","mapBorder":"rgba(82, 0, 0, 0.8)","nicknameFill":"rgba(179, 194, 255, 1)","nicknameStroke":"rgba(14, 15, 22, 1)","serverFill":"rgba(241, 224, 70, 1)","serverStroke":"rgba(14, 15, 22, 1)","adminLevelFill":"rgba(46, 46, 209, 1)","discordCopiedFill":"rgba(78, 183, 107, 1)","monitoringFill":["rgba(163, 99, 46, 1)","rgba(49, 140, 115, 1)"],"playerFill":"rgba(191, 143, 84, 1)","playerStroke":"rgba(82, 82, 82, 1)"},"defaultFont":"Aldrich, sans-serif"}');
    var s = function(t, e) {
        let i = null;
        return i = arguments[0] instanceof o ? new o(arguments[0].x, arguments[0].y) : "number" == typeof arguments[0] && void 0 === arguments[1] ? new o(arguments[0], arguments[0]) : "number" == typeof arguments[0] && "number" == typeof arguments[1] ? new o(t, e) : new o(0, 0), i
    };
    class n {
        constructor(t = 0, e = 0) {
            this.x = t, this.y = e
        }
        static random2D(t, e = 1) {
            return new n(e * Math.cos(t), e * Math.sin(t))
        }
        get magnitude() {
            return Math.sqrt(this.x ** 2 + this.y ** 2)
        }
        get copy() {
            return new n(this.x, this.y)
        }
        getRotate(t) {
            return new n(this.x * Math.cos(t) - this.y * Math.sin(t), this.x * Math.sin(t) + this.y * Math.cos(t))
        }
        getProject(t) {
            const e = t.direction.x * (this.x - t.origin.x) + t.direction.y * (this.y - t.origin.y);
            return new n(t.origin.x + t.direction.x * e, t.origin.y + t.direction.y * e)
        }
        getAdd(t, e) {
            const i = s(t, e);
            return new n(this.x + i.x, this.y + i.y)
        }
        getMinus(t, e) {
            const i = s(t, e);
            return new n(this.x - i.x, this.y - i.y)
        }
        getMult(t, e) {
            const i = s(t, e);
            return new n(this.x * i.x, this.y * i.y)
        }
        setMag(t) {
            return this.normalize().mult(t)
        }
        different(t, e) {
            const i = s(t, e);
            return new n(this.x - i.x, this.y - i.y)
        }
        set(t, e) {
            const i = s(t, e);
            return this.x = i.x, this.y = i.y, this
        }
        add(t, e) {
            const i = s(t, e);
            return this.x += i.x, this.y += i.y, this
        }
        sub(t, e) {
            const i = s(t, e);
            return this.x -= i.x, this.y -= i.y, this
        }
        mult(t, e) {
            const i = s(t, e);
            return this.x *= i.x, this.y *= i.y, this
        }
        div(t, e) {
            const i = s(t, e);
            return this.x /= i.x, this.y /= i.y, this
        }
        mulScalar(t) {
            const e = s(t);
            return this.x *= e.x, this.y *= e.y, this
        }
        normalize() {
            const t = this.magnitude;
            return t <= 0 ? this : new n(this.x, this.y).div(t || 1)
        }
        projection(t) {
            const e = t.normalize(),
                i = this.mulScalar(t);
            return e.mult(i), e
        }
        clamp(t, e) {
            return this.x = Math.max(t.x, Math.min(e.x, this.x)), this.y = Math.max(t.y, Math.min(e.y, this.y)), this
        }
        floor() {
            return this.x = Math.floor(this.x), this.y = Math.floor(this.y), this
        }
        dot(t) {
            return this.x * t.x + this.y * t.y
        }
        cross(t) {
            return this.x * t.y - this.y * t.x
        }
        lengthSq() {
            return this.x * this.x + this.y * this.y
        }
        length() {
            return Math.sqrt(this.x * this.x + this.y * this.y)
        }
        lerp(t, e) {
            return this.x += (t.x - this.x) * -e, this.y += (t.y - this.y) * -e, this
        }
        lerpVectors(t, e, i) {
            return this.x = t.x + (e.x - t.x) * i, this.y = t.y + (e.y - t.y) * i, this
        }
        distanceTo(t, e) {
            const i = s(t, e);
            return this.copy.sub(i).length()
        }
        angleTo(t, e) {
            const i = s(t, e).copy.sub(this);
            return Math.atan2(i.y, i.x)
        }
        random() {
            return this.x = Math.random(), this.y = Math.random(), this
        }
        reset() {
            return this.x = 0, this.y = 0, this
        }
        log() {
            console.log(this.x, this.y)
        }
    }
    var o = n;
    var r = class {
        constructor({
            x: t,
            y: e,
            dx: i,
            dy: s
        }) {
            this.origin = new o(t, e), this.direction = new o(i, s)
        }
    };
    var h = class {
        constructor(t, e, i = 5, s = .9) {
            this.mass = i, this.time = s, this.position = new o(t, e), this.velocity = new o, this.acceleration = new o, this.force = new o, this.position.lastX = this.position.x, this.position.lastY = this.position.y, this.velocity.lastX = this.velocity.x, this.velocity.lastY = this.velocity.y
        }
        updatePhysics() {
            this.position.lastX = this.position.x, this.position.lastY = this.position.y, this.velocity.lastX = this.velocity.x, this.velocity.lastY = this.velocity.y, this.force.div(this.mass), this.acceleration.add(this.force.x, this.force.y), this.acceleration.mult(this.time), this.velocity.add(this.acceleration.x, this.acceleration.y), this.velocity.mult(this.time), this.position.add(this.velocity.x, this.velocity.y)
        }
        resetPhysics() {
            this.force.reset(), this.acceleration.reset(), this.velocity.reset()
        }
    };
    class a extends h {
        constructor(t, e, i, s) {
            s = s || i, super(t, e), this.width = i || 0, this.height = s || 0
        }
        get x() {
            return this.position.x
        }
        get y() {
            return this.position.y
        }
        get lastX() {
            return this.position.lastX - this.width / 2
        }
        get lastY() {
            return this.position.lastY - this.height / 2
        }
        set x(t) {
            this.position.set(t + this.width / 2, this.position.y)
        }
        set y(t) {
            this.position.set(this.position.x, t + this.height / 2)
        }
        get clone() {
            return new a(this.position.x, this.position.y, this.width, this.height)
        }
        setTo(t, e) {
            const i = s(t, e);
            this.position.set(i)
        }
        copyFrom(t) {
            this.setTo(t.position.x, t.position.y)
        }
        copyTo(t) {
            t.setTo(t.position.x, t.position.y)
        }
        distanceTo(t, e) {
            t instanceof a && (t = new o(t.x, t.y));
            const i = s(this.x, this.y),
                n = s(t, e);
            return i.distanceTo(n)
        }
        angleTo(t, e) {
            t instanceof a && (t = new o(t.x, t.y));
            const i = s(this.x, this.y),
                n = s(t, e);
            return i.angleTo(n)
        }
    }
    var c = a;
    var d = class {
        constructor({
            x: t,
            y: e,
            width: i,
            height: s,
            angle: n
        }) {
            this.center = new o(t, e), this.size = new o(i, s), this.angle = n
        }
        getAxis() {
            const t = new o(1, 0),
                e = new o(0, 1),
                i = t.getRotate(this.angle),
                s = e.getRotate(this.angle);
            return [new r({
                x: this.center.x,
                y: this.center.y,
                dx: i.x,
                dy: i.y
            }), new r({
                x: this.center.x,
                y: this.center.y,
                dx: s.x,
                dy: s.y
            })]
        }
        getCorners() {
            const t = this.getAxis(),
                e = t[0].direction.getMult(this.size.x / 2),
                i = t[1].direction.getMult(this.size.y / 2);
            return [this.center.getAdd(e).getAdd(i), this.center.getAdd(e).getAdd(i.getMult(-1)), this.center.getAdd(e.getMult(-1)).getAdd(i.getMult(-1)), this.center.getAdd(e.getMult(-1)).getAdd(i)]
        }
    };
    var l = function(t, e, i) {
        const s = i.getProject(e).getMinus(t.center),
            n = s.x * e.direction.x + s.y * e.direction.y > 0;
        return s.magnitude * (n ? 1 : -1)
    };
    var u = class {
        constructor() {
            this._events = new Map
        }
        has(t) {
            return this._events.has(t)
        }
        on(t, e) {
            const i = this._events.get(t);
            i ? i.push(e) : this._events.set(t, [e])
        }
        emit(t, ...e) {
            this._events.has(t) && this._events.get(t).forEach((t => {
                t(...e)
            }))
        }
    };
    String.prototype.toNumber = function() {
        return parseFloat(this)
    }, String.prototype.toPixels = function() {
        const t = this.toNumber();
        return `${t<0?0:t}px`
    }, Number.prototype.toString = function() {
        return String(this)
    }, Number.prototype.toPixels = function() {
        return `${this<0?0:this}px`
    }, Math.lerp = function(t, e, i) {
        return t + (e - t) * i
    }, Math.randomFloat = function(t, e) {
        return void 0 === e && (e = t, t = 0), Math.random() * (e - t + 1) + t
    }, Math.randomAngle = function() {
        return Math.randomFloat(-Math.PI, Math.PI)
    }, CanvasRenderingContext2D.prototype.fillCircle = function(t, e, i) {
        this.beginPath(), this.arc(t, e, i, 0, 2 * Math.PI), this.fill(), this.closePath()
    }, CanvasRenderingContext2D.prototype.strokeCircle = function(t, e, i) {
        this.beginPath(), this.arc(t, e, i, 0, 2 * Math.PI), this.stroke(), this.closePath()
    };
    var g = Object.assign({
        Emitter: u,
        wait(t) {
            return new Promise((e => setTimeout(e, t)))
        }
    }, e);
    class y extends g.Point {
        static textDraws = [];
        constructor(t, e, i, s, n, o, r, h, a, c, d) {
            super(e, i, 0, 0), this.text = t, this.fontSize = s, this.fillColor = n, this.strokeColor = o, this.isBold = r, this.letterSpacing = h, this.rotation = a * (Math.PI / 180), this.backgroundColor = c, this.padding = 0 === d ? d : d || 6
        }
        getMetrics() {
            A.save(), this.setDrawStyles();
            const t = A.measureText(this.text),
                e = t.actualBoundingBoxAscent + t.actualBoundingBoxDescent;
            return A.restore(), {
                width: t.width,
                height: e
            }
        }
        setDrawStyles() {
            A.font = `${this.isBold?"bold ":""}${this.fontSize.toPixels()} ${D.defaultFont}`, A.strokeStyle = this.strokeColor, A.lineWidth = 8, A.textBaseline = "middle", A.textAlign = "center", A.lineJoin = "round", A.lineCap = "round", A.letterSpacing = this.letterSpacing.toPixels()
        }
        draw() {
            A.save(), this.setDrawStyles();
            const t = this.getMetrics();
            A.translate(this.x - R.getXOffset(), this.y - R.getYOffset()), A.rotate(this.rotation), this.backgroundColor && (A.fillStyle = this.backgroundColor, A.beginPath(), A.roundRect(-t.width / 2 - this.padding, -t.height / 2 - this.padding, t.width + 2 * this.padding, t.height + 2 * this.padding, 8), A.fill()), A.fillStyle = this.fillColor, A.strokeText(this.text, 0, 0), A.fillText(this.text, 0, 0), A.restore()
        }
        update() {
            this.draw()
        }
        static addTextDraw(...t) {
            for (const e of t) y.textDraws.push(e)
        }
        static updateAllTextDraws() {
            for (const t of y.textDraws) t.update()
        }
    }
    class x extends g.Point {
        static buttonBoxes = [];
        constructor(t) {
            const e = t instanceof y ? t.getMetrics() : t,
                i = t.x - e.width / 2,
                s = t.y - e.height / 2;
            super(i - t.padding, s - t.padding, e.width + 2 * t.padding, e.height + 2 * t.padding), this.boxDraw = t, this.events = new g.Emitter, this.isClicked = !1, this.isHovered = !1, this.isReadyForClick = !1
        }
        checkIsHover() {
            const t = this.x - R.getXOffset(),
                e = this.y - R.getYOffset();
            return F.x >= t && F.x <= t + this.width && F.y >= e && F.y <= e + this.height
        }
        checkIsClick() {
            return !!this.isHovered && (this.isReadyForClick && !F.isMouseDown ? (this.isReadyForClick = !1, this.events.emit("click"), !0) : F.isMouseDown ? (this.isReadyForClick = !0, !1) : void 0)
        }
        update() {
            const t = this.boxDraw instanceof y ? this.boxDraw.getMetrics() : this.boxDraw,
                e = this.boxDraw.x - t.width / 2,
                i = this.boxDraw.y - t.height / 2;
            this.setTo(e - this.boxDraw.padding, i - this.boxDraw.padding), this.isClicked = this.checkIsClick(), this.isHovered = this.checkIsHover(), this.isHovered || (this.isReadyForClick = !1)
        }
        static addButtonBox(...t) {
            for (const e of t) x.buttonBoxes.push(e)
        }
        static updateAllButtonBoxes() {
            for (const t of x.buttonBoxes) t.update();
            return !x.buttonBoxes.every((t => !t.isHovered)) ? F.setType("button") : V.isReadyMove ? F.setType("dragging") : void F.setType("canvas")
        }
    }
    class p extends g.Point {
        static types = {
            canvas: "default",
            button: "pointer",
            dragging: "grab"
        };
        constructor() {
            super(D.map.width / 2, D.map.height / 2, 0, 0), this.type = "canvas", this.isMouseDown = !1
        }
        getType() {
            return this.type
        }
        setType(t) {
            this.type = t;
            const e = p.types[this.type];
            R.view.style.cursor !== e && (R.view.style.cursor = e)
        }
    }

    function m(t, e) {
        if (!(e instanceof Function)) return !1;
        const i = this.layers[t];
        return i.set(i.size + 1, e)
    }

    function w() {
        for (const t in this.layers) {
            this.layers[t].forEach((t => {
                t()
            }))
        }
    }

    function f() {}
    class v extends g.Emitter {
        static delta = 0;
        static currentUpdateTime = 0;
        static lastUpdateTime = 0;
        constructor(t) {
            super(), this.tiedScene = t, this.layers = new Array(3).fill((() => null)).map((() => new Map)), this.on("init", f.bind(this)), this.on("add-render", m.bind(this)), this.on("update-layers", w.bind(this))
        }
        update() {
            const t = this.tiedScene.getRenderContext();
            t.save(), t.clearRect(0, 0, this.tiedScene.getScaledWidth(), this.tiedScene.getScaledHeight()), this.emit("update-layers", 0), t.restore()
        }
        static onFrame(t) {
            v.currentUpdateTime = Date.now(), v.delta = v.currentUpdateTime - v.lastUpdateTime, v.lastUpdateTime = v.currentUpdateTime, t(), requestAnimationFrame(v.onFrame.bind(v, t))
        }
    }
    class S extends g.Point {
        constructor() {
            super(D.map.width / 2, D.map.height / 2, 0, 0), this.xVel = 0, this.yVel = 0
        }
        isMove() {
            return Boolean(this.xVel || this.yVel)
        }
        collideBorders() {
            this.x < 0 && (this.x = 0), this.x > D.map.width && (this.x = D.map.width), this.y < 0 && (this.y = 0), this.y > D.map.height && (this.y = D.map.height)
        }
        decelVelocity() {
            this.xVel && (this.xVel *= Math.pow(.993, v.delta), this.xVel <= .01 && this.xVel >= -.01 && (this.xVel = 0)), this.yVel && (this.yVel *= Math.pow(.993, v.delta), this.yVel <= .01 && this.yVel >= -.01 && (this.yVel = 0))
        }
        update() {
            this.isMove() && (this.x += this.xVel, this.y += this.yVel, this.decelVelocity(), this.collideBorders())
        }
    }
    class b extends g.Point {
        static imageBoxes = [];
        constructor(t, e, i, s) {
            super(e, i, s, s), this.imageSrc = t, this.image = new Image, this.image.src = this.imageSrc, this.image.onload = () => {
                this.image.isLoaded = !0
            }, this.padding = 0
        }
        draw() {
            this.image.isLoaded && (A.save(), A.translate(this.x - R.getXOffset(), this.y - R.getYOffset()), A.drawImage(this.image, -this.width / 2, -this.height / 2, this.width, this.height), A.restore())
        }
        update() {
            this.draw()
        }
        static addImageBox(...t) {
            for (const e of t) b.imageBoxes.push(e)
        }
        static updateAllImageBoxes() {
            for (const t of b.imageBoxes) t.update()
        }
    }
    class M extends g.Point {
        constructor(t) {
            super(0, 0, 0, 0), this.tiedScene = t, this.xOffset = 0, this.yOffset = 0
        }
        follow(t) {
            const e = this.distanceTo(t),
                i = this.angleTo(t),
                s = Math.min(.01 * e * v.delta, e);
            e > .05 ? (this.x += s * Math.cos(i), this.y += s * Math.sin(i)) : this.setTo(t.x, t.y), this.xOffset = this.x - this.tiedScene.getScaledWidth() / 2, this.yOffset = this.y - this.tiedScene.getScaledHeight() / 2
        }
    }

    function T() {
        const t = this.getRenderContext();
        t.save(), t.fillStyle = D.colors.map, t.fillRect(0, 0, this.getScaledWidth(), this.getScaledHeight()), t.restore()
    }
    let k = null;

    function P() {
        k || (k = new y("Copied!", W.x + W.width / 2, W.y + 1.5 * W.height, 24, D.colors.discordCopiedFill, D.colors.nicknameStroke, !1, 2)), k.update()
    }
    class C extends g.Emitter {
        constructor(t) {
            super(), this.tiedScene = t, this.on("draw-background", T.bind(this.tiedScene)), this.on("draw-text-copied", P.bind(this.tiedScene))
        }
    }

    function z() {
        const t = window.innerWidth,
            e = window.innerHeight,
            i = this.getRenderContext(),
            s = Math.max(t / (this.viewport.width * this.getZoom()), e / (this.viewport.height * this.getZoom()));
        this.setScale(s), this.setSize(t, e), i.scale(s, s)
    }

    function B() {
        this.emit("scene-resize"), this.renderer.emit("init"), this.renderer.emit("add-render", D.SYSTEM_LAYER, (() => {
            this.camera.follow(V), this.drawing.emit("draw-background")
        })), this.renderer.emit("add-render", D.ENTITIES_LAYER, (() => {
            V.update(), y.updateAllTextDraws(), x.updateAllButtonBoxes(), b.updateAllImageBoxes()
        })), this.renderer.emit("add-render", D.ESP_LAYER, (() => {
            W.lastShowTextCopied && (Date.now() - W.lastShowTextCopied > 750 ? W.lastShowTextCopied = null : this.drawing.emit("draw-text-copied"))
        })), window.addEventListener("resize", (() => this.emit("scene-resize")))
    }
    class E extends g.Emitter {
        constructor(t, e) {
            super(), this.view = document.querySelector(t), this.scale = 1, this.viewport = e || D.defaultViewport, this.renderer = new v(this), this.camera = new M(this), this.drawing = new C(this), this.on("init", B.bind(this)), this.on("scene-resize", z.bind(this))
        }
        getRenderContext() {
            return this.view.getContext("2d")
        }
        getScale() {
            return this.scale
        }
        getZoom() {
            return this.viewport.zoom
        }
        getXOffset() {
            return this.camera.xOffset
        }
        getYOffset() {
            return this.camera.yOffset
        }
        getWidth() {
            return this.view.width
        }
        getHeight() {
            return this.view.height
        }
        getScaledWidth() {
            return this.getWidth() / this.getScale()
        }
        getScaledHeight() {
            return this.getHeight() / this.getScale()
        }
        setScale(t) {
            "string" == typeof t && (t = t.toNumber()), this.scale = t
        }
        setZoom(t) {
            "string" == typeof t && (t = t.toNumber()), this.viewport.zoom = t, this.emit("scene-resize")
        }
        setSize(t, e) {
            this.view.width = t, this.view.height = e, this.view.style.width = t.toPixels(), this.view.style.height = e.toPixels()
        }
    }
    const D = i,
        R = new E("#main_canvas"),
        A = R.getRenderContext(),
        F = new p,
        V = new S,
        L = new y("NUDO", D.map.middleSize[0] + 10, D.map.middleSize[1] - 200, 120, D.colors.nicknameFill, D.colors.nicknameStroke, !0, 20),
        Y = new y("Administrator 4 level", D.map.middleSize[0] + 1, D.map.middleSize[1] - 140, 24, D.colors.adminLevelFill, D.colors.nicknameStroke, !1, 2, 0, null, 8),
        O = new y("Главный следящий за МО", D.map.middleSize[0] + 1, D.map.middleSize[1] - 113, 18, D.colors.monitoringFill[0], D.colors.nicknameStroke, !1, 2, 0, null, 8),
        _ = new y("", D.map.middleSize[0] + 1, D.map.middleSize[1] - 90, 18, D.colors.monitoringFill[1], D.colors.nicknameStroke, !1, 2, 0, null, 8),
        I = new y("Sun City", D.map.middleSize[0] + 1, D.map.middleSize[1] + 49, 26, D.colors.serverFill, D.colors.serverStroke, !1, 2, 0, null, 0),
        H = new b("./images/vkicon.png", -999, -999, 35),
        X = new b("./images/discordicon.png", -999, -999, 38),
        N = new b("./images/forumicon.png", -999, -999, 30),
        j = new x(I),
        U = new x(H),
        W = new x(X),
        Z = new x(N);

    function q(t) {
        F.isMouseDown = !0, V.isReadyMove || (F.setTo(t.clientX / R.getScale(), t.clientY / R.getScale()), V.isReadyMove = !0, V.startPoint = new g.Point(F.x, F.y, 0, 0))
    }

    function $(t) {
        F.isMouseDown = !1, V.isReadyMove = !1, V.startPoint = null
    }

    function J(t) {
        if (F.setTo(t.clientX / R.getScale(), t.clientY / R.getScale()), !V.isReadyMove) return;
        const e = F.angleTo(V.startPoint),
            i = V.startPoint.distanceTo(F),
            s = Math.min(35e-6 * i * v.delta, i);
        V.xVel = s * v.delta * Math.cos(e), V.yVel = s * v.delta * Math.sin(e)
    }

    function G(t, e) {
        const i = R.getZoom(),
            s = .05 !== e;
        if (!(i >= t))
            for (let n = 0; n < 5; n++) setTimeout((() => {
                if (i >= t) return;
                let n = i + Math.lerp(e, i, e);
                s && (n = i * e), R.setZoom(n)
            }), 5 * n)
    }

    function K(t, e) {
        const i = R.getZoom(),
            s = .05 !== e;
        if (!(i <= t))
            for (let n = 0; n < 5; n++) setTimeout((() => {
                if (i <= t) return;
                let n = i - Math.lerp(e, i, e);
                s && (n = i / e), R.setZoom(n)
            }), 5 * n)
    }
    y.addTextDraw(L, Y, O, _, I), x.addButtonBox(j, U, W, Z), b.addImageBox(H, X, N), W.lastShowTextCopied = null,
        function() {
            const t = D.map.middleSize[0] - 45 * (b.imageBoxes.length / 2 - .5);
            for (let e = 0; e < b.imageBoxes.length; e++) {
                b.imageBoxes[e].setTo(t + 45 * e + 1, D.map.middleSize[1] + 82)
            }
        }(), window.addEventListener("touchstart", (t => q(t.touches[0])), !1), window.addEventListener("mousedown", (t => q(t)), !1), window.addEventListener("touchend", $, !1), window.addEventListener("mouseup", $, !1), window.addEventListener("touchmove", (t => J(t.touches[0])), !1), window.addEventListener("mousemove", (t => J(t)), !1);
    let Q = !1,
        tt = null;

    function et() {
        window.open("https://forum.arizona-rp.com/forums/1986/", "__blank")
    }

    function it() {
        window.open("https://vk.com/nohak", "__blank")
    }

    function st() {
        W.lastShowTextCopied = Date.now(), navigator.clipboard.writeText("nudoo")
    }

    function nt() {
        window.open("https://forum.arizona-rp.com/members/1735841/", "__blank")
    }
    window.addEventListener("touchmove", (t => {
        if (2 === t.touches.length) {
            const e = new g.Point(t.touches[0].pageX, t.touches[0].pageY),
                i = new g.Point(t.touches[1].pageX, t.touches[1].pageY),
                s = e.distanceTo(i),
                n = Math.abs(s - tt);
            if (V.isReadyMove = !1, null != tt && n >= 5 || Q) {
                const t = Number(s > tt);
                Q = !0, t ? K(.1, 1.1) : G(2, 1.1)
            }
            tt = s
        }
    })), window.addEventListener("touchstart", (() => {
        tt = null, Q = !1
    })), window.addEventListener("touchend", (() => {
        tt = null, Q = !1
    })), window.addEventListener("wheel", (t => {
        if (t.deltaY > 0) return G(2, .05);
        K(.1, .05)
    }), !1), window.addEventListener("load", (() => {
        R.emit("init"), j.events.on("click", et), U.events.on("click", it), W.events.on("click", st), Z.events.on("click", nt), v.onFrame((() => {
            R.renderer.update()
        }))
    }), !1)
}();
//# sourceMappingURL=bundle.js.map
